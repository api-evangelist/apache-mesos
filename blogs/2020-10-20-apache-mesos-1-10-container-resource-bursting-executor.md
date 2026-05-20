---
title: "Apache Mesos 1.10: Container Resource Bursting, Executor Domain Sockets, V1 Operator API Performance, and Reservation Update"
url: "/blog/mesos-1-10-0-released/"
date: "2020-10-20T00:00:00+00:00"
author: "Benjamin Mahler"
feed_url: "https://mesos.apache.org/blog/feed"
---
We are excited to announce that Apache Mesos 1.10.0 has been released! Along with lots of bug fixes and improvements, the following are the larger items: New Features and Improvements Container Resource Bursting Mesos now supports per-container CPU and memory usage beyond the allocation to the container, up to a configured limit. Previously, it was only possible to enable CPU bursting for all (or none) of the containers on the agent, without per-container control.
