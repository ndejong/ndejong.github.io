---
layout: post
title: Hack a phone, hack a bank
author: Nicholas de Jong
excerpt: <p>Complex systems are hard to secure.  It's a statement that gets made time and time again and it makes perfect sense.  If you have a system where interactions between various components is complex and difficult to describe or monitor then you can be sure that the failure of components within that system will have consequences that are hard to foresee or appreciate.  No surprise.</p>
---

### July 10, 2018
This post was written ~10 years ago and it's another area where not much has improved, perhaps become even worse.  Of
note is the more recent mobile-carrier support for VoIP over LTE which is giving rise to a whole range of "old" VoIP 
attack vectors reappearing all over again.

****

### May 22, 2009
Complex systems are hard to secure.  It's a statement that gets made time and time again and it makes perfect sense.  If 
you have a system where interactions between various components is complex and difficult to describe or monitor then 
you can be sure that the failure of components within that system will have consequences that are hard to foresee or 
appreciate.  No surprise.

Thus is the case with recent online banking applications that raise the security bar by issuing one-time-passwords 
for high-value money transactions via mobile phone based test messages.  The idea is a good one but relying on it is a 
bad idea.

![nokia-1100](/images/posts/2009-05-22/Nokia_1100.jpg "nokia-1100")

It turns out that our Nokia 1100 has had its firmware broken in a manner such that it is [possible to re-program](http://www.alibaba.com/product/gsmrnet-10801587-10621506/Flash_IC_N323GT7MI_For_Nokia_1100.html)
both the phone IMEI (International Mobile Equipment Identity) and more importantly the IMSI (International Mobile 
Subscriber Identity) number that the phone reports to the network.  With the ability to change the IMSI it is hence 
possible to "own" any number you wish.

You might think this sounds great because you can prank friends pretending to be someone else.  You'd be right but there 
are much easier ways to achieve this by exploiting a whole host of [VoIP vulnerabilities](http://www.google.com/search?q=voip+registration+hijack).
The real power of this ability lays in the fact that you will also **receive** data bound for that IMSI and this means 
you will receive inbound text messages.

... and there's the problem.  Our imaginary bad guy obtains your online banking credentials.  Chances are if he/she 
manages to obtain this level of information they will have also gleaned your phone number and a host of other personal 
information, this is often possible with [botnet based keyboard loggers](http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9128280).
With online banking details in hand it is now possible to action a wire transfer and receive the associated one-time 
password to complete the transaction.  Don't worry, it will happen faster than you'll be able to action to prevent it.

Security involving technology is complex because the failure of one small part has many knock-on effects that are 
difficult to see.  In this case it appears the ability to decrypt the Nokia 1100 firmware was the thin edge of the wedge 
that led to a chain of possibilities exposing this particular form of online banking security.

The exposures for this vulnerability almost certainly run deeper than online banking applications as there are a range 
of systems that work this way including various physical access protection systems. 

Should we panic, probably not, but we should take the time to understand the risk and act accordingly.

A few other articles related to the matter:
 - [Investigators replicate Nokia 1100 online banking hack](http://www.thestandard.com/news/2009/05/21/investigators-replicate-nokia-1100-online-banking-hack)
 - [Nokia: We don't know why criminals want our old phones](http://www.thestandard.com/news/2009/04/21/nokia-we-dont-know-why-criminals-want-our-old-phones)

