---
title: "Run Mesos Locally with Mesos Mini Docker Container"
url: "/blog/mesos-mini/"
date: "2018-11-19T00:00:00+00:00"
author: "Jie Yu"
feed_url: "https://mesos.apache.org/blog/feed.xml"
---
<p><a href="https://hub.docker.com/r/mesos/mesos-mini/">Mesos Mini</a> is a Docker image maintained by the Apache Mesos community.
It allows you to test Mesos locally with a simple <code>docker run</code>.</p>

<h1>Why Mesos Mini</h1>

<p>Being able to spin up a local Mesos cluster in Docker can greatly simplify the work in the following scenarios:</p>

<ul>
<li><em>Demo</em>: Imagine doing a live demo with Mesos in a conference with unstable Wifi.</li>
<li><em>Framework development</em>: Write end-to-end integration tests for your framework with a local Mesos cluster in a Docker container.
This can be easily automated in your test suite.</li>
<li><em>Test new Mesos features</em>: Test new features from Mesos that haven&rsquo;t been released yet.
You might be able to do that by building Mesos from the source code, but most framework developers do not know how to do it, and it is slow.</li>
</ul>


<p>The idea is similar to <a href="https://github.com/kubernetes/minikube">minikube</a> or <a href="https://github.com/ContainerSolutions/minimesos">minimesos</a>.</p>

<p>However, <a href="https://github.com/ContainerSolutions/minimesos">minimesos</a> is no longer maintained.
As a result, Apache Mesos community decides to maintain a solution in Mesos repository to simplify CI integrations.</p>

<h1>Get started</h1>

<p>Make sure <a href="https://docs.docker.com/install/">Docker</a> is installed.
We have tested on both Linux and MacOS.</p>

<p>To create a local Mesos cluster, simply do a <code>docker run</code>:</p>

<pre><code class="bash">$ docker run --rm --privileged -p 5050:5050 -p 5051:5051 -p 8080:8080 mesos/mesos-mini
</code></pre>

<p>It will launch one Mesos master, one Mesos agent, and one example framework (Marathon) in the Docker container.</p>

<p>You should be able to access Mesos master UI at <code>http://localhost:5050</code>.
Similarly, you can access Mesos agent at <code>http://localhost:5051</code>.
Marathon UI can be accessed at <code>http://localhost:8080</code>.</p>

<p>You should be able to launch containers in the local Mesos cluster using Marathon like the following:</p>

<pre><code class="bash">$ cat app.json
{
  "id": "test",
  "cmd": "sleep 1000",
  "cpus": 1,
  "mem": 128,
  "disk": 0,
  "instances": 1,
  "container": {
    "docker": {
      "image": "alpine"
    },
    "type": "DOCKER"
  },
  "networks": [
    {
      "mode": "host"
    }
  ]
}
$ curl -X POST -d @app.json -H "Content-type: application/json" http://localhost:8080/v2/apps
</code></pre>

<p>To stop the local Mesos cluster, please use <code>docker stop</code>.
All artifacts associated with the local Mesos cluster will be cleaned up when the Docker container stops.</p>

<p>The following Docker image tags are maintained:</p>

<ul>
<li><code>master</code>: The latest master branch HEAD.</li>
<li><code>&lt;RELEASE_BRANCH&gt;</code>: The latest release branch HEAD (e.g., <code>1.7.x</code>).</li>
<li><code>master-&lt;DATE&gt;</code>: The snapshot builds for master branch (e.g., <code>master-2018-11-19</code>).</li>
<li><code>&lt;RELEASE_BRANCH&gt;-&lt;DATE&gt;</code>: The snapshot builds for release branch (e.g., <code>1.7.x-2018-11-19</code>).</li>
</ul>


<p>Note that there is no support for release branches earlier than <code>1.7.x</code>.
All future release branches will be supported.</p>

<h1>How is it done?</h1>

<h2>Manage multiple services</h2>

<p>We use <code>systemd</code> to manage multiple daemons in the Mesos Mini Docker container.
As a result, you can use the following command to restart the Mesos master in the Mesos Mini Docker container:</p>

<pre><code class="bash">$ docker exec &lt;CONTAINER_ID&gt; systemctl restart mesos-master
</code></pre>

<p>Similarly, you can use that to restart other services (e.g., Mesos agent or Marathon).
This is very useful for those end-to-end integration tests that want to simulate Mesos master failover.</p>

<h2>Docker Containerizer</h2>

<p>One of the goals of Mesos Mini is to mimic production settings as much as possible.</p>

<p>To allow frameworks to launch Docker containers, we embed a Docker Daemon (i.e., Docker in Docker) in the Mesos Mini Docker container.
For instance, to view all Docker containers in the Mesos cluster, use the following command on your host:</p>

<pre><code class="bash">$ docker exec &lt;CONTAINER_ID&gt; docker ps
</code></pre>

<p>The cgroup root for the embedded Docker Daemon has been configured so that the cgroups for the nested Docker containers are properly nested within the Mesos Mini Docker container.
This ensures that no cgroups traces will be left in the system when the Mesos Mini Docker container finishes.</p>

<h2>Mesos Containerizer (UCR)</h2>

<p>For Mesos Containerizer (UCR), we turn on most of the <a href="https://github.com/apache/mesos/docs/mesos-containerizer.md">isolators</a> that are typically turned on in production environments.
Similar to Docker daemon, we need to do a few tweaking on cgroups in Mesos Mini Docker container to make sure it does not leave any traces when Mesos Mini Docker container terminates.</p>

<p>For each cgroup subsystem, Docker does a bind mount from the current cgroup to the root of the cgroup subsystem.
For instance:</p>

<pre><code class="bash">/sys/fs/cgroup/memory/docker/&lt;cid&gt; -&gt; /sys/fs/cgroup/memory
</code></pre>

<p>This will confuse Mesos agent and UCR because it relies on proc file <code>/proc/&lt;pid&gt;/cgroup</code> to determine the cgroups of a given process, and this proc file is not affected by the bind mount of the cgroups.</p>

<p>To workaround that, we perform the following steps for each cgroup subsystems when bootstrapping the Mesos Mini Docker container to recreates the cgroups layout as if it were on the host.</p>

<pre><code class="bash">$ mkdir -p /sys/fs/cgroup/memory/docker/&lt;cid&gt;
$ mount --bind /sys/fs/cgroup/memory /sys/fs/cgroup/memory/docker/&lt;cid&gt;
</code></pre>

<p>And then set Mesos agent <code>--cgroups_root</code> flag to <code>docker/&lt;cid&gt;</code>.</p>

<h1>Maintenance</h1>

<p>The <a href="https://github.com/apache/mesos/tree/master/support/mesos-mini">build scripts</a> for Mesos Mini is hosted in Mesos repository.
The <a href="https://builds.apache.org/view/M-R/view/Mesos/job/Docker/job/Mini/">Mesos Docker Mini Jenkins CI</a> has been setup to automatically push daily snapshot builds to Docker hub for supported release branches as well as the master branch.</p>

<p>For any bug fix or new features, please follow the <a href="http://mesos.apache.org/community/#contribute-a-patch">Apache Mesos contribution guide</a>.</p>

<h2>Mesos CentOS Docker Image</h2>

<p>In some scenarios, some users might prefer having a Docker image that only has Mesos installed.
To enable that, we also built a <code>mesos/mesos-centos</code> Docker image.
The tags are similar to those of Mesos Mini.
In fact, <code>mesos/mesos-mini</code> uses <code>mesos/mesos-centos</code> as its base image.</p>

<p>The <a href="https://github.com/apache/mesos/tree/master/support/packaging/centos/build-docker-centos.sh">build scripts</a> for Mesos CentOS Docker image is also hosted in Mesos repository.
The <a href="https://builds.apache.org/view/M-R/view/Mesos/job/Docker/job/CentOS/">Mesos Docker CentOS Jenkins CI</a> has been setup to automatically push daily snapshot builds to Docker hub for supported release branches as well as the master branch.</p>

<h1>Current limitations</h1>

<ul>
<li>Only one Mesos agent can be launched in the Mesos Mini Docker container.</li>
<li>Marathon uses in-memory storage instead of ZK.</li>
<li>SSL is not enabled.</li>
</ul>
