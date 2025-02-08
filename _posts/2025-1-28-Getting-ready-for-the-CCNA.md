---
layout: post
title: "Wrapping up the CCNA course"
description: "Finishing our CCNA prep course"
date: 2025-01-26
feature_image: images/ccna_route_origination_tunnels.png
tags: [traineeship, work, cybersecurity, cisco, ccna, networking]
---
So that wraps it up, weeks 2 and 3 flew by! Our prep course for the Cisco CCNA has finished. Savnet instructors Arthur and Adrian did an awesome job covering everything in the [CCNA 200-301 syllabus](), so big shoutout to them.

Learning how to actually implement infrastructure, like using STP to prevent Layer 2 looping, securing networks with things like port-security, access lists, ARP inspection, and DHCP snooping was pretty interesting, not gonna lie! But I’ll also admit, I was definitely ready for a break. Over the past three weeks, I studied for at least 7 hours in the Savnet classes and then 2-3 more hours at home or in the office. Staying late and arriving early helped me avoid the crazy Dutch rush hours (zo drukke)! But honestly, it was a memorable and valuable experience.

### Pulling it all together in our final lab

Towards the end of the course, we thought, "Ah, we know this, exam in the bag, easy peasy." That was before Arthur ramped up the pace with some labs that were *a little* more fun. By fun, I mean difficult. And by a little, I mean just a wee bit (which is Irish for *a lot* ). Our final lab was a co-***lab***-orative effort. Okay, promise that's the last dad joke for now.

Our high-level overview was to implement a multi-branch infrastructure, with multiple VLANs connected via a mix of multilayer switches, ether-channels, and a bunch of other configurations. This included IPv4 DHCP servers per branch, route sharing through a single-area OSPF backbone, and an adjacent GRE WAN tunnel. The WAN also used an underlay with EIGRP to facilitate the tunnel. Within each branch, we configured Per VLAN STP to designate primary and secondary root bridges and set up trunks and access links, considering security and the configured etherchannel links. We also included port-security with two sticky MAC addresses allowed per access interface, along with restrict violation and portfast with BPDU Guard. Fault tolerance was another focus, so we used FHRP to create a virtual default gateway for each VLAN. The etherchannel was set up using the open standard LACP, and the design itself helps reduce risk by creating multiple Layer 2 and 3 paths. There's probably some other features I'm forgetting as well, after a while it became more difficult to track the changes as there were so many. Goes to show the importance of a good implementation checklist!

### Troubleshooting

{% include image_caption.html imageurl="/images/ccna_recap_lab.jpg" title="Recap Lab" caption="This was one of our final labs, trying to use as many technologies as possible." %}

Here’s a pic of the topology we worked on together (note the pretty fonts and colors). One of the things we struggled with in this design was setting up a logging and NTP server. For some reason, it just wouldn’t work. We spent hours troubleshooting NTP and Syslog and finally decided our setup was fine, and GNS3 was the culprit. We restarted the instance, swapped out a few virtual switches, and *voilà!* We finally had lovely trapped logs appearing on our Linux server. GNS3 was a great tool to learn the Cisco IOS CLI, but it definitely had its buggy moments. We all started poking fun at the issues and came up with creative ways to track how many virtual devices we managed to break. Below are some examples of the fun we had with the labs.

{% include image_caption.html imageurl="/images/ccna_lab_sinbin.png" title="The Sinbin Lab" caption="In this lab, GCS3 had issues with several switches, so I decided to swap them out." %}

{% include image_caption.html imageurl="/images/ccna_hell_gravyard.png" title="Graveyard Lab" caption="Victor and Luuk had similar issues, but they got a bit superstitious, so they buried their 'dead' devices instead." %}

{% include image_caption.html imageurl="/images/ccna_acls_qos_batman.png" title="QoS and ACL Lab" caption="Eventually, we sorted our issues and moved on to QoS and ACL integrated labs." %}

Overall, the course was awesome, and the ON2IT team was always there to help us. The Savnet team also made sure we understood everything. Arthur in particular was so keen for us to learn it was common for him to insist we think of more questions for him! But, I’m sure we'll have plenty of questions for him during our next revision next week!
