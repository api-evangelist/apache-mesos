---
title: "Apache Mesos 1.8.1 Released"
url: "/blog/mesos-1-8-1-released/"
date: "2019-07-29T00:00:00+00:00"
author: "Benno Evers"
feed_url: "https://mesos.apache.org/blog/feed.xml"
---
<p>The latest Mesos 1.8.x release, 1.8.1, is now available for <a href="http://mesos.apache.org/downloads">download</a>. This release includes important bug fixes and improvements on top of 1.8.0. It is recommended to use this version if you are considering using Mesos 1.8. More specifically, this release includes the following:</p>

<ul>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9395">MESOS-9395</a> - Check failure on <code>StorageLocalResourceProviderProcess::applyCreateDisk</code>.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9616">MESOS-9616</a> - <code>Filters.refuse_seconds</code> declines resources not in offers.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9730">MESOS-9730</a> - Executors cannot reconnect with agents using TLS1.3</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9750">MESOS-9750</a> - Agent V1 <code>GET_STATE</code> response may report a complete executor&rsquo;s tasks as non-terminal after a graceful agent shutdown.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9766">MESOS-9766</a> - /<strong>processes</strong> endpoint can hang.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9779">MESOS-9779</a> - <code>UPDATE_RESOURCE_PROVIDER_CONFIG</code> agent call returns 404 ambiguously.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9782">MESOS-9782</a> - Random sorter fails to clear removed clients.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9786">MESOS-9786</a> - Race between two <code>REMOVE_QUOTA</code> calls crashes the master.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9803">MESOS-9803</a> - Memory leak caused by an infinite chain of futures in <code>UriDiskProfileAdaptor</code>.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9831">MESOS-9831</a> - Master should not report disconnected resource providers.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9852">MESOS-9852</a> - Slow memory growth in master due to deferred deletion of offer filters and timers.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9856">MESOS-9856</a> - REVIVE call with specified role(s) clears filters for all roles of a framework.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9870">MESOS-9870</a> - Simultaneous adding/removal of a role from framework&rsquo;s roles and its suppressed roles crashes the master.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9695">MESOS-9695</a> - Remove the duplicate pid check in Docker containerizer</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9759">MESOS-9759</a> - Log required quota headroom and available quota headroom in the allocator.</li>
<li><a href="https://issues.apache.org/jira/browse/MESOS-9787">MESOS-9787</a> - Log slow SSL (TLS) peer reverse DNS lookup.</li>
</ul>


<p>Full release notes are available in the release <a href="https://gitbox.apache.org/repos/asf?p=mesos.git;a=blob_plain;f=CHANGELOG;hb=1.8.1">CHANGELOG</a></p>

<h3>Upgrades</h3>

<p>Rolling upgrades from a Mesos 1.8.0 cluster to Mesos 1.8.1 are straightforward. Please refer to the <a href="http://mesos.apache.org/documentation/latest/upgrades/">upgrade guide</a> for detailed information on upgrading to Mesos 1.8.1 from 1.7.x, 1.6.x, or 1.5.x.</p>

<h3>Try it out</h3>

<p>Please try out this release and let us know what you think. If you run into any issues, let us know on the <a href="https://mesos.apache.org/community">user mailing list and/or Slack/IRC</a>.</p>

<h3>Thanks!</h3>

<p>Thanks to the 9 contributors who made 1.8.1 possible:</p>

<p>Andrei Budnik, Andrei Sekretenko, Benjamin Mahler, Chun-Hung Hsiao, Gilbert Song, Joseph Wu, Meng Zhu, Qian Zhang, Stéphane Cottin</p>
