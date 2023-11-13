---
layout: post
title: Autossh plugin for OPNsense
author: Nicholas de Jong
---

The Autossh plugin for OPNsense was submitted as a [pull-request](https://github.com/opnsense/plugins/pull/818) for
consideration to be added as another OPNsense plugin.

Autossh plugin for OPNsense is a tool for establishing, maintaining and managing reliable 
SSH tunnels with remote hosts. It can be used to solve a wide range of connection challenges 
through the (sometimes creative) use of TCP port-forwards.

## Features
 - Default ssh-key permissions that prevent unwanted remote ssh-server shell access abuses.
 - Ability to define local-forward and remote-forward TCP tunnels.
 - Ability to define local network SOCKS proxy via a remote host (aka dynamic-forward).
 - Ability to bind outbound ssh connections to different (external) interfaces.
 - Ability to configure many (27x) of the ssh-client connection parameters, including all cryptographic options.
 - Ability to observe the health status of the tunnel at a glance.
 - Can rely on Autossh to reestablish a tunnel after a connectivity outage.

## Use cases
 - Provide remote network access to a site that has no public addresses, such as when ISPs use NAT.
 - Ensure redundant multipath remote access via primary and secondary connections via interface binding.
 - Create your own "privacy" VPN system for all local network users using a SOCKS proxy (dynamic-forward) to a remote system.
 - Provide local network access to remote system services such as a SMTP relay or another SSH service.
 - Provide remote system access to a local network services such as a database or RDP service.
 - Provide access remote system access to other remote network acting as a middle-man TCP-port connector.

## Screen shots
![opnsense-plugin-autossh-01](/images/posts/opnsense-autossh/opnsense-plugin-autossh-01.png "opnsense-plugin-autossh-01")
![opnsense-plugin-autossh-03](/images/posts/opnsense-autossh/opnsense-plugin-autossh-03.png "opnsense-plugin-autossh-03")
![opnsense-plugin-autossh-04](/images/posts/opnsense-autossh/opnsense-plugin-autossh-04.png "opnsense-plugin-autossh-04")

## Source
Check out code [github.com/verbnetworks/opnsense-plugin-autossh](https://github.com/verbnetworks/opnsense-plugin-autossh)
