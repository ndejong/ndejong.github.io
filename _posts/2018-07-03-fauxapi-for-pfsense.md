---
layout: post
title: FauxAPI for pfSense
author: Nicholas de Jong
excerpt: <p>A few years ago I ended up with responsibility for a small fleet of pfSense hosts in several different countries with some being 400+ms latency away which made managing them difficult.  I was keen to find a solution that would save staff time and provide a way achieve better configuration consistency across them.  After taking a good look at the pfSense code the complexities of the code legacy pfSense is dealing with made it clear why there was no existing API for pfSense as the webapp do not have a consistent framework or Model-View-Control arrangement, indeed many operations simply happen inline at page load.</p>
---

A few years ago I ended up with responsibility for a small fleet of pfSense hosts in several different countries with 
some being 400+ms latency away which made managing them difficult.  I was keen to find a solution that would save staff 
time and provide a way achieve better configuration consistency across them.  After taking a good look at the pfSense 
code the complexities of the code legacy pfSense is dealing with made it clear why there was no existing API for 
pfSense as the webapp do not have a consistent framework or Model-View-Control arrangement, indeed many operations 
simply happen inline at page load.
  
This is not a dig at pfSense, it all makes sense when you consider the rich history and pfSense backstory, but it meant 
the prospects of reining in the effort required to manage all those pfSense hosts was going to be less straight-forward 
than I had wanted.  What I realised however was that many of the tasks that needed some form of automation could 
(probably) be achieved via direct edits to the system `config.xml` file with a reload action, and thus FauxAPI came about.


**From the documentation**  
> ## Approach
> At its core FauxAPI simply reads the core pfSense config.xml file, converts it to JSON and returns to the API 
> caller. Similarly it can take a JSON formatted configuration and write it to the pfSense config.xml and handles 
> the required reload operations. The ability to programmatically interface with a running pfSense host(s) is enormously 
> useful however it should also be obvious that this provides the API user the ability to create configurations that 
> can break your pfSense system.
>
> FauxAPI provides easy backup and restore API interfaces that by default store configuration backups on all 
> configuration write operations thus it is very easy to roll-back even if the API user manages to deploy a "very 
> broken" configuration.
>
> Multiple sanity checks take place to make sure a user provided JSON config will correctly convert into the (slightly 
> quirky) pfSense XML config.xml format and then reload as expected in the same way. However, because it is not a 
> real per-action application-layer interface it is still possible for the API caller to create configuration changes 
> that make no sense and can potentially disrupt your pfSense system - as the package name states, it is a "Faux" API 
> to pfSense filling a gap in functionality with the current pfSense product.


FauxAPI has been going for several years now and is starting to develop a small community around it with various
other projects depending on it:
 * [www.softfire.eu/](https://www.softfire.eu/)
 * [github.com/EpaL/kindercontrol](https://github.com/EpaL/kindercontrol)
 * [community.home-assistant.io/t/pfsense-stat-monitor/61070](https://community.home-assistant.io/t/pfsense-stat-monitor/61070)
 * [github.com/ndejong/pfsense_fauxapi_client_python](https://github.com/ndejong/pfsense_fauxapi_client_python)
 * [github.com/ndejong/pfsense_fauxapi_client_bash](https://github.com/ndejong/pfsense_fauxapi_client_bash)
 * [github.com/Elucidia/faux-api-client](https://github.com/Elucidia/faux-api-client)
 * [npmjs.com/package/pfsense-fauxer](https://www.npmjs.com/package/pfsense-fauxer)
 * [github.com/travisghansen/pfsense_fauxapi_php_client](https://github.com/travisghansen/pfsense_fauxapi_php_client)

### Releases
 * [v1.3 announcement](https://www.reddit.com/r/PFSENSE/comments/8vt1zt/fauxapi_v13_released_a_rest_api_interface_for/)
 * [v1.2 announcement](https://www.reddit.com/r/PFSENSE/comments/6wjeyi/fauxapi_a_rest_api_interface_for_pfsense_to/)
 * [v1.1 announcement](https://forum.netgate.com/topic/108433/fauxapi-a-rest-based-api-for-pfsense)

### Github
 * [https://github.com/ndejong/pfsense_fauxapi](https://github.com/ndejong/pfsense_fauxapi)

Perhaps one of these days the pfSense team will have time/resources to review the FauxAPI code to accept my Pull Request 
into their FreeBSD ports tree:-
 * [https://github.com/pfsense/FreeBSD-ports/pull/531](https://github.com/pfsense/FreeBSD-ports/pull/531)
 
Until then, you can easily install it manually - see the documentation.
