---
title: "Apache Mesos 1.7.1 Released"
url: "/blog/mesos-1-7-1-released/"
date: "2019-01-28T00:00:00+00:00"
author: "Chun-Hung Hsiao & Gastón Kleiman"
feed_url: "https://mesos.apache.org/blog/feed.xml"
---
<p>Apache Mesos 1.7.1 is now available for <a href="http://mesos.apache.org/downloads">download</a>. As we continue to focus on performance, the community can get access to the latest performance improvements in this release. The <a href="http://mesos.apache.org/documentation/latest/csi/">experimental support for Container Storage Interface (CSI)</a> has been improved in this release as well. Last but not least, this release includes 38 bug fixes to 1.7.0. If you are considering using Mesos 1.7, it is recommended to use 1.7.1.</p>

<p>Specifically, the following critical bugs are resolved in this release:</p>

<ul>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9131">MESOS-9131</a> - Health checks launching nested containers while a container is being destroyed lead to unkillable tasks.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9228">MESOS-9228</a> - SLRP does not clean up plugin containers after it is removed.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9279">MESOS-9279</a> - Docker Containerizer &lsquo;usage&rsquo; call might be expensive if mount table is big.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9281">MESOS-9281</a> - SLRP gets a stale checkpoint after system crash.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9283">MESOS-9283</a> - Docker containerizer actor can get backlogged with large number of containers.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9308">MESOS-9308</a> - URI disk profile adaptor could deadlock.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9317">MESOS-9317</a> - Some master endpoints do not handle failed authorization properly.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9334">MESOS-9334</a> - Container stuck at ISOLATING state due to libevent poll never returns.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9419">MESOS-9419</a> - Executor to framework message crashes master if framework has not re-registered.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9474">MESOS-9474</a> - Master does not respect authorization result for <code>CREATE_DISK</code> and <code>DESTROY_DISK</code>.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9480">MESOS-9480</a> - Master may skip processing authorization results for <code>LAUNCH_GROUP</code>.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9501">MESOS-9501</a> - Mesos executor fails to terminate and gets stuck after agent host reboot.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9502">MESOS-9502</a> - IOswitchboard cleanup could get stuck due to FD leak from a race.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9508">MESOS-9508</a> - Official 1.7.0 tarball can&rsquo;t be built on Ubuntu 16.04 LTS.</li>
</ul>


<p>And this release includes the following critical improvements:</p>

<ul>
<li><a href="https://issues.apache.org/jira/browse/MESOS-6765">MESOS-6765</a> - &ldquo;Make the Resources wrapper &rdquo;&ldquo;copy-on-write&rdquo;&ldquo; to improve performance.&rdquo;</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9239">MESOS-9239</a> - Improve sorting performance in the DRF sorter.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9249">MESOS-9249</a> - Avoid dirtying the DRF sorter when allocating resources.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9275">MESOS-9275</a> - Allow optional <code>profile</code> to be specified in <code>CREATE_DISK</code> offer operation.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9305">MESOS-9305</a> - Create cgoup recursively to workaround systemd deleting cgroups_root.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9321">MESOS-9321</a> - Add an optional <code>vendor</code> field in <code>Resource.DiskInfo.Source</code>.</li>
</ul>


<p>Full release notes are available in the release <a href="https://gitbox.apache.org/repos/asf?p=mesos.git;a=blob_plain;f=CHANGELOG;hb=1.7.1">CHANGELOG</a>.</p>

<h3>Upgrades</h3>

<p>Rolling upgrades from a Mesos 1.7.0 cluster to Mesos 1.7.1 are straightforward. However, if your framework is consuming the <a href="http://mesos.apache.org/documentation/latest/csi/">experimental support for CSI</a>, the language binding used by the framework should be updated.</p>

<p>For detailed information on upgrading to Mesos 1.7.1 from other versions, please refer to the <a href="http://mesos.apache.org/documentation/latest/upgrades/">upgrade guide</a>.</p>

<h3>Try it out</h3>

<p>Please try out this release and let us know what you think. If you run into any issues, let us know on the <a href="https://mesos.apache.org/community">user mailing list and/or Slack/IRC</a>.</p>

<h3>Thanks!</h3>

<p>Thanks to the 20 contributors who made 1.7.1 possible:</p>

<p>Alexander Rojas, Alexander Rukletsov, Andrei Budnik, Benjamin Bannier, Benjamin Mahler, Benno Evers, Chun-Hung Hsiao, Deepak Goel, Gastón Kleiman, Gilbert Song, Greg Mann, James Peach, Jie Yu, Joseph Wu, Kevin Klues, Meng Zhu, Qian Zhang, Till Toenshoff, Vinod Kone, Fei Long</p>
