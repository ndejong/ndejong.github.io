---
layout: post
title: Getting The Blog Back Online
author: Nicholas de Jong
---

After a ~10 year hiatus I've found time return the blog online - happy days.  After considering various approaches I've 
settled on using Github Pages which provides a several nice upsides with least one very-notable downside.

I spent a small amount of time checking out the various Python based options currently out there and had all but settled 
on [Mezzanine](http://mezzanine.jupo.org/)  maintained by a Sydney based [Google developer](https://github.com/stephenmcd).

While Mezzanine is an awesome tool the Github Pages / Jekyll approach means one less web-server to concern myself with, 
which suits me just fine.

Something that really helped convince me Github Pages was a reasonable and respectable approach was noticing that 
[Twitter Bootstrap](https://github.com/twbs/bootstrap) uses Github Pages to publish their content and documentation. 

### Upsides
 - no database required, everything is static.
 - content version control is obviously built in and part of the deal
 - Github Pages are served via their CDN provider, Fastly - check out the DNS query/response
   ```bash
    $ dig +noall +answer blog.nicholasdejong.com
    blog.nicholasdejong.com. 468	IN	CNAME	ndejong.github.io.
    ndejong.github.io.	2715	IN	CNAME	sni.github.map.fastly.net.
    sni.github.map.fastly.net. 30	IN	A	151.101.9.147
   ```

### Downsides
 - have to deal with learning Jekyll
 - ~~not possible to serve pages over HTTPS on a CNAME redirected domain, which really sucks~~ - it would really be nice 
   if Github Pages could be served via HTTPS however if you think this through it would imply having to share a trusted 
   certificate with an external party, aka Github, which in turn draws unwanted attention on Github as the custodians of 
   many HTTPS certificates.
 - the Github issue-thread for support of HTTPS is [here](https://github.com/isaacs/github/issues/156)
 - NB: as of 2018-05-01 Github are [now supporting HTTPS](https://blog.github.com/2018-05-01-github-pages-custom-domains-https/) 
   for custom domains so the major downside here has gone away

I've had time in the past few weeks to dredge up some limited posts from my blog which I've been slowly adding back 
again, surprising how much of the security matters are still relevant today.
