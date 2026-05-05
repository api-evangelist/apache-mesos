---
title: "Apache Mesos 1.8: Allocator Performance, Seccomp Isolation and Operation Feedback"
url: "/blog/mesos-1-8-0-released/"
date: "2019-05-02T00:00:00+00:00"
author: "Benno Evers"
feed_url: "https://mesos.apache.org/blog/feed.xml"
---
<p>We&rsquo;re pleased to announce that Mesos 1.8.0 is now available for <a href="/downloads">download</a>.</p>

<p>As usual, lots of work and care went into this release, with a total of 255 JIRA issues resolved,
and 1149 commits containing a total diffstat of 656 files changed, 62213 insertions(+) and 20403 deletions(-).</p>

<pre><code> 4.9% 3rdparty/
       1.5% 3rdparty/libprocess/
       1.6% 3rdparty/stout/
 2.3% docs/
 2.5% include/
 2.0% site/
77.4% src/
       7.8% src/csi/
       3.6% src/examples/
      11.0% src/master/
       4.2% src/resource_provider/
      10.3% src/slave/
      28.8% src/tests/
6.7% support/
       3.7% support/python3/
</code></pre>

<p>Looking at the distribution of changes, nearly all components have seen major activity.
Some of that is presented in more detail below.</p>

<p>One major focus for the 1.8 contributors seems to have been solid test coverage, with
nearly one third of the total amount of lines changed being inside the test suite.</p>

<h2>Highlights</h2>

<h3>Allocator Performance Improvements</h3>

<p>In Mesos 1.8, allocator cycle time is significantly decreased when quota is
used; around 40% for a small size cluster and up to 70% for larger clusters.
This greatly narrows the allocator performance gap between quota and non-quota
usage scenarios.</p>

<p>In addition, schedulers can now specify the minimum resource quantities needed
in an offer, which acts as an override of the global <code>--min_allocatable_resources</code>
master flag. Updating schedulers to specify this field improves multi-scheduler
scalability as it reduces the amount of offers declined from having insufficient
resource quantities.</p>

<p>Note that this feature currently requires that the scheduler re-subscribes each
time it wants to mutate the minimum resource quantity offer filter information,
see <a href="https://issues.apache.org/jira/browse/MESOS-7258">MESOS-7258</a>.</p>

<h3>Seccomp Isolator</h3>

<p>A new <code>linux/seccomp</code> <a href="docs/isolators/linux-seccomp">isolator</a> was added. This
isolator makes use of the
<a href="https://www.kernel.org/doc/Documentation/prctl/seccomp_filter.txt">seccomp</a>
facility provided by recent linux kernels.</p>

<p>Using this isolator, containers launched by Mesos containerizer can be sandboxed
by enabling filtering of system calls using a configurable policy.</p>

<h3>Operation Feedback</h3>

<p>In Mesos 1.6, operation feedback was introduced for operations on resources
by a resource provider.</p>

<p>In Mesos 1.8, v1 schedulers can now receive operation feedback for operations
on agent default resources, i.e. normal cpu, memory, and disk. This means that
the v1 scheduler API&rsquo;s operation feedback feature can now be used for any offer
operations except for <code>LAUNCH</code> and <code>LAUNCH_GROUP</code>, on any type of resources.</p>

<h3>Containerization</h3>

<p>A number of containerization-related improvements have landed in Mesos 1.8:</p>

<ul>
<li><p>Support pulling docker images with docker manifest
V2 Schema2 on Mesos Containerizer.</p></li>
<li><p>Support custom port range option to the <code>network/ports</code>
isolator. Added the <code>--container_ports_isolated_range</code> flag to the
<code>network/ports</code> isolator. This allows the operator to specify a custom
port range to be protected by the isolator.</p></li>
<li><p>Support XFS quota for persistent volumes. Added
persistent volume support to the <code>disk/xfs</code> isolator.</p></li>
<li><p>Support an option to create non-existing host
paths for host path volume in Mesos Containerizer. Added a new
agent flag <code>--host_path_volume_force_creation</code> for the
<code>volume/host_path</code> isolator.</p></li>
</ul>


<h3>CLI Improvements</h3>

<p>The Mesos CLI now offers the task subcommand with two actions. The first
action, <code>task attach</code>, allows you to attach your terminal to a running
task launched with a tty. The second action, <code>task exec</code>, launches a
new nested container inside a running task.</p>

<p>To build the CLI, use the flag <code>--enable-new-cli</code> with Autotools or
<code>-DENABLE_NEW_CLI=1</code> with CMake on MacOS or Linux.</p>

<h3>Experimental Features</h3>

<p>Mesos 1.8 adds experimental support for the new CSI v1 API. Operators can deploy
plugins that are compatible to either CSI v0 or v1 to create persistent
volumes through storage local resource providers, and Mesos will
automatically detect which CSI versions are supported by the plugins.</p>

<h2>Upgrade</h2>

<p>Upgrades from Mesos 1.7.0 to Mesos 1.8.0 should be straightforward. Please
refer to the <a href="http://mesos.apache.org/documentation/latest/upgrades/">upgrade guide</a>
for detailed information on upgrading to Mesos 1.8.0.</p>

<ul>
<li>Frameworks relying on the experimental <code>RECONCILE_OPERATIONS</code> call can
not be updated to Mesos 1.8, since the API of that has been reworked in
a non-backwards compatible manner.</li>
</ul>


<h2>Credits</h2>

<p>Finally, a big <strong>THANK YOU</strong> goes out to all the 49 patch authors who made the 1.8.0 release possible:</p>

<p>Aaron Wood, Alexander Rojas, Alexander Rukletsov, Andrei Budnik, Andrei Sekretenko, Andrew Schwartzmeyer,
Armand Grillet, Benjamin Bannier, Benjamin Hindman, Benjamin Mahler, Benno Evers, Chun-Hung Hsiao,
Clement Michaud, Deepak Goel, Dominik Dary, Dragos Schebesch, Eric Chung, Fei Long, Gastón Kleiman,
Gilbert Song, Greg Mann, Ilya Pronin, Jacob Janco, James DeFelice, James Peach, Jan Schlicht,
Jason Lai, Jie Yu, Joseph Wu, Kapil Arya, Kevin Klues, Liangyu Zhao, Meng Zhu, Michael Park, Michał Łowicki,
Packt, Pavel Kirillov, Qian Zhang, Robin Gögge, Se Choi, Senthil Kumaran, Sergey Urbanovich, Tad Guo
Till Toenshoff, Tomasz Janiszewski, Vinod Kone, Xudong Ni</p>
