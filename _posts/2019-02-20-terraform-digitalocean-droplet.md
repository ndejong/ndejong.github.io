---
layout: post
title: Terraform + Digital Ocean Droplets
author: Nicholas de Jong
---

This Terraform module creates a Digital Ocean Droplet using Terraform with desirable 
additional features.  The module is essentially a wrapper around the Digital Ocean 
provider using a `cloudinit` script to provide additional features:-
 * remount existing volumes
 * create an initial user with an sshkey

### Update
2022-03-28 - the source for this module has been migrated from github **verbnetworks** to
github **ndejong** - the module at **registry.terraform.io** points to verbnetworks which is
redirected to ndejong - yeeeee.

Current version is now v0.2.1

## Source
 * [github.com/ndejong/terraform-digitalocean-droplet](https://github.com/ndejong/terraform-digitalocean-droplet)

## Terraform Module
 * [registry.terraform.io/modules/ndejong/droplet/digitalocean](https://registry.terraform.io/modules/verbnetworks/droplet/digitalocean)
