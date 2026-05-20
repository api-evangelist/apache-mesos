---
title: "Apache Mesos 1.2.0 Released"
url: "/blog/mesos-1-2-0-released/"
date: "2017-03-08T00:00:00+00:00"
author: "Adam"
feed_url: "https://mesos.apache.org/blog/feed"
---
The latest Mesos release, 1.2.0, is now available for download . This release includes the following features and improvements: MESOS-5931 - Experimental support for auto backend in Mesos Containerizer, prefering overlayfs then aufs. Please note that the bind backend needs to be specified explicitly through the agent flag --image_provisioner_backend since it requires the sandbox already existed.
