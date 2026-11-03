+++
date = '2026-11-03T16:10:00-05:00'
draft = false
title = 'Securing a dual-site consumer DVR system'
description = "Locking down security camera access and video archival via implementing a site-to-site VPN in consumer hardware"
+++

# Background

I was presented with an existing IP security camera system deployed to two sites, connected to a DVR in one of the sites. The DVR software was responsible for archiving captured security footage as well as presenting a dashboard to access live camera feeds.

To manage remote access to the DVR, its management interface was port-forwarded to the public internet. To manage access between the DVR and the cameras not on its site, all the cameras were port-forwarded to the public internet as well.

