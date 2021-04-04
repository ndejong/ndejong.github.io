---
layout: post
title: Experiments With Cjdns
author: Nicholas de Jong
---

In December, 2017 I spent time experimenting with a mesh overlay network called [Cjdns](https://github.com/cjdelisle/cjdns)
that has some interesting qualities about it.  I'm not a fan of the darkside-crypto-anarchy mentality that 
pervades some of the [Hyperboria](https://hyperboria.net/) network participants as I believe it erodes the 
legitimacy of the technology in the same way as Torrent and Tor peer-to-peer systems have issues.  With an 
information-security-hat on however it's a technology to understand because among other things it can very 
easily bridge networks in ways you probably do not care for in your own environment.

There are several key concepts with Cjdns that when bought together that make it rather neat indeed, however 
the "thing" that I find most interesting is the approach to the address-allocation and key-verification.

## Address allocation and keys
Cjdns is built on IPv6 networking which means you might need to (or rather I needed to) get over anxieties 
about growing up from an IPv4 world.  The choice of IPv6 by Cjdns is important because the self-allocated 
IPv6 addresses are entangled with the node public key which tightly-couples addresses with public-keys and 
in-turn means network participants implicitly know that a public-key is the correct key for an IPv6 
address.  This very nicely deals with the key-distribution and verification hassles without needing any 
kind of central authority etc.

This is achieved by generating many private/public keypairs doing a double-sha512 on the first 16 bytes 
of the public-key until the result starts with **FC** which then forms the IPv6 address.

The following pseudo code describes the process 
```
while ipv6_address is None:
    private_key, public_key = generate_private_public_keypair()
    ipv6_address_attempt = sha512(sha512(public_key[0:16]))
    if ipv6_address_attempt[0:2] == 'FC':
        ipv6_address = ipv6_address_attempt
```
Because the FC00::/8 address space is allocated as a IPv6 local-address space the network hence has an 
address space to operate within.

This leads to a natural question about brute-forcing the entire address-space. To put this into perspective 
this would mean computing key-pairs and hence IPv6 address of 16^(32-2) ~= 1.329E+36 addresses which if 
you are going to attempt you'll want to store so you don't have to re-compute.  If we estimate 160 bytes 
per address (ipv6-address + public-key + private-key) as plain-text (non-optimal) then you'll require 
something like 1.9E+26 petabytes of storage which means you'll spend your entire time filling out AWS 
limit increase request forms - this is a very back of the envelope analysis and addresses the storage 
requirements without regard for any compute requirement, either way it would seem that brute forcing to 
obtain a given Cjdns node IPv6 address is probably difficult enough in 2018.

## Network visualization
You can observe the scale of the Hyperboria network built using Cjdns at [fc00.org](https://www.fc00.org/), there 
are a few interesting nodes to observe:-
 - the IPFS gateway nodes h.gateway.ipfs.io/1 to 4 which is particularly interesting for [sites hosted on IPFS](https://ipfs.io/docs/examples/example-viewer/example#../websites/README.md) in my view.
 - the mega peer at h.magik6k.net operated by [magik6k](https://github.com/magik6k)
 - peer "5d11" that is stuck at cjdns version-16 with a deep family of children nodes all also on v16 - this node has 
   been in place since at least 2016-03-21 if the Google search results for the full IPv6 address are correct.

## Experimenting with it
Because Cjdns is just an overlay network it means you can simply fire up the daemon, attach to a [public-peer](https://github.com/hyperboria/peers) 
and you are connected - that simplicity breeds hazard - consider what happens in an enterprise environment 
when your clever staff fire up a cjdns-node from an internal position, suddenly you are bridged and it can 
be rather difficult to manage even with restrictive firewalls and IDS/IPS systems in-place.

My initial concern in attaching anything to the Cjdns network was that it represents a whole new 
unregulated network where anything can happen with very limited recourse - this coupled with having to 
come up-to-speed with IPv6 at the same time made me uneasy so I settled on a plan to run the Cjdns node 
daemon on a temporary cloud-hosted compute provider where the bandwidth is plentiful and less bad things 
happen if the host somehow becomes compromised.

This in turn led me to check out several alternative cloud-hosting providers other than AWS, namely 
Softlayer, Azure, Alicloud and Digital Ocean where it became apparent the metric that mattes the most 
is the cost of traffic - the best options seem to be Digital Ocean and Alicloud when compared on this basis.

| Provider      | $USD/TB | Notes |
| ---           | ---     | ---   |
| AWS           | $90.00  | US East 1 + extra for compute instance |
| Softlayer     | $45.00  | Requires monthly contract, pain in the arse to deal with + extra for compute instance |
| Azure         | $88.65  | US West + extra for compute instance |
| Alicloud      | $4.50   | 1TB transfer included on minimum instance size |
| Digital Ocean | $5.00   | 1TB transfer included on minimum instance size |

I ended up writing a Terraform module for Digital Ocean to quickly fire up instances running Cjdns which you can get 
for yourself here:-
 * [github.com/ndejong/terraform-digitalocean-cjdns-node](https://github.com/ndejong/terraform-digitalocean-cjdns-node)

## Thoughts and outcomes
The Cjdns protocol itself is fine enough, but the flagship Hyperboria network that uses it lacks any DNS system which 
makes the network difficult to use because there is no (or limited) discoverability of network services.  There seem to 
be proposals for a block-chain based DNS system which aligns with the decentralized aspirations of the Hyperboria 
community but host naming is just part of the problem-set.  Content discoverability (aka a search engine) within the 
network would seem to be the greater challenge that requires real resources to address.

After running a cluster of 6x nodes (2x Singapore, 2x New York, 2x San Francisco) for a week where each peer was cross
peered with each other and then publicly peered with ~8x lowest-latency peers relative to each region the total traffic 
levels were quite small with less than 10's of GB of traffic over than time.  I neglected to record the actual 
statistics at the time so I'll need to redo and track this more carefully.

My sense is to write AWS and Alicloud Terraform modules and run a longer experiment across all three providers and 
examine more carefully the nature of the traffic - bearing in mind traffic content is entirely opaque unless such 
traffic is bound for your node.

If you have an interest in peering with me do get in contact.

Reminder to self, check out the exit.li nodes:-
 * [https://github.com/kpcyrd/exit.li](https://github.com/kpcyrd/exit.li)
