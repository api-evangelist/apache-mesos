---
title: "Apache Mesos 1.5.3 Released"
url: "/blog/mesos-1-5-3-released/"
date: "2019-03-19T00:00:00+00:00"
author: "Gilbert Song"
feed_url: "https://mesos.apache.org/blog/feed.xml"
---
<p>The latest Mesos 1.5.x release, 1.5.3, is now available for <a href="http://mesos.apache.org/downloads">download</a>. This release includes important bug fixes and improvements on top of 1.5.0. It is recommended to use this version if you are considering using Mesos 1.5. More specifically, this release includes the following:</p>

<ul>
<li><a href="https://issues.apache.org/jira/browse/MESOS-7474">MESOS-7474</a> - Mesos fetcher cache doesn&rsquo;t retry when missed.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-8887">MESOS-8887</a> - Unreachable tasks are not GC'ed when unreachable agent is GC'ed.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-8907">MESOS-8907</a> - Docker image fetcher fails with HTTP/2.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9210">MESOS-9210</a> - Mesos v1 scheduler library does not properly handle SUBSCRIBE retries.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9305">MESOS-9305</a> - Create cgoup recursively to workaround systemd deleting cgroups_root.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9317">MESOS-9317</a> - Some master endpoints do not handle failed authorization properly.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9332">MESOS-9332</a> - Nested container should run as the same user of its parent container by default.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9334">MESOS-9334</a> - Container stuck at ISOLATING state due to libevent poll never returns.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9362">MESOS-9362</a> - Test <code>CgroupsIsolatorTest.ROOT_CGROUPS_CreateRecursively</code> is flaky.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9411">MESOS-9411</a> - Validation of JWT tokens using HS256 hashing algorithm is not thread safe.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9492">MESOS-9492</a> - Persist CNI working directory across reboot.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9507">MESOS-9507</a> - Agent could not recover due to empty docker volume checkpointed files.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9518">MESOS-9518</a> - CNI_NETNS should not be set for orphan containers that do not have network namespace.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9532">MESOS-9532</a> - ResourceOffersTest.ResourceOfferWithMultipleSlaves is flaky.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9533">MESOS-9533</a> - CniIsolatorTest.ROOT_CleanupAfterReboot is flaky.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9555">MESOS-9555</a> - Allocator CHECK failure: reservationScalarQuantities.contains(role).</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9581">MESOS-9581</a> - Mesos package naming appears to be undeterministic.</li>
</ul>


<p>Full release notes are available in the release <a href="https://gitbox.apache.org/repos/asf?p=mesos.git;a=blob_plain;f=CHANGELOG;hb=1.5.3">CHANGELOG</a></p>

<h3>Upgrades</h3>

<p>Rolling upgrades from a Mesos 1.5.0 cluster to Mesos 1.5.3 are straightforward. Please refer to the <a href="http://mesos.apache.org/documentation/latest/upgrades/">upgrade guide</a> for detailed information on upgrading to Mesos 1.5.3 from 1.4.x, 1.3.x, or 1.2.x.</p>

<h3>Try it out</h3>

<p>Please try out this release and let us know what you think. If you run into any issues, let us know on the <a href="https://mesos.apache.org/community">user mailing list and/or Slack/IRC</a>.</p>

<h3>Thanks!</h3>

<p>Thanks to the 7 contributors who made 1.5.3 possible:</p>

<p>Andrei Budnik, Benjamin Mahler, Gilbert Song, Jie Yu, Qian Zhang, Till Toenshoff, Vinod Kone</p>
