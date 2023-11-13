---
layout: post
title: Motorcycle ride from New York to San Francisco
author: Nicholas de Jong
excerpt: <p>Moto as in motorbike and motorcycle.  Riding from New York City to San Francisco and blogging about it on the way has been the underlaying motivation to put this site together in the first-place.  I'm planning on doing the ride in June  2009 on a Kawasaki KLR650 over the course of 4 weeks.</p>
---

### July 10, 2018 - Looking back in time.
In the Summer of 2009 I rode a Kawasaki KLR650 motorcycle from New York City to San Francisco via Canada.  This post 
pieces together several original posts that describe the preparations for the adventure and the technology that was 
modern then.  When it came to actually doing the journey I "posted" my adventure using a GPS tracker, with a script that 
took the lat/log converted it into location names using a Geocoding API and then posted a short sentence/statement 
about where I was on [Twitter](https://twitter.com/onamoto) which was cross connected to my Facebook at the time.

![onamoto-1](/images/posts/2008-12-29/IMG_2875.JPG "onamoto-1")

****

### December 28, 2008 - Motorcycle ride from New York to San Francisco
Moto as in motorbike and motorcycle.  Riding from New York City to San Francisco and blogging about it on the way has 
been the underlaying motivation to put this site together in the first-place.  I'm planning on doing the ride in June 
2009 on a Kawasaki KLR650 over the course of 4 weeks.

Such a ride would not be complete without plans to keep a daily blog to be posted herewith.  The daily blog capability 
is already implemented but the next trick is to establish something that keeps my GPS location updated on a Google map 
together with snapshot images from a bike mounted camera.  Sounds ambitious at this stage and whether I can put together 
equipment that will survive the journey and not get in the way remains to be seen.  At this early stage things are 
looking good though, I've already identified the components I plan to use and I'm ready to get them ordered.

****

### December 29, 2008  - The route from New York to San Francisco on a motorcycle
![google-maps-static](/images/posts/2008-12-29/google-maps-static.png "google-maps-static")

Rough list of cities and places I plan to visit and or pass through:
 - New York City
 - Philadelphia
 - Baltimore
 - Washington DC
 - Monongahela National Forest
 - Charlston
 - Daniel Boone National Forest
 - Hooster National Forest
 - St Louis
 - Kansas City
 - a long boring ride...
 - Denver
 - Colorado Springs
 - Capital Reef National Park
 - Grand Canyon National Park
 - Las Vegas
 - Death Valley National Park
 - Santa Barbara
 - Highway 1
 - San Francisco

The way I came up with my route was quite literally to request from Google Maps a route from New York City to San Francisco 
avoiding highways and tollways to make things interesting.   From there I've observed the map and tried to bend the 
route so I go through as many forests and green parts as possible.

The only problem I've run into is that I seem to have hit a limit in terms of the points Google Maps will allow me to 
add to the route, for the technical people out there they'll understand me when I say it looks like the HTTP string is 
simply getting too long and won't take any more additional GET parameters.  I intend to resolve this my simply splitting 
the route into two sections.

There is a useful Google Maps thing feature I've discovered recently though and that is the ability to save (and even 
share) maps with routes into "My Maps".  This turns out to be rather useful and more manageable than generating a route 
and saving the URL that defines the map.

I guess the other tool I expect to be very useful is the Garmin Zumo 550 Motorcycle Navigator because while the route I 
have posted here appears very exact with lefts and rights and turns all calculated out it's surely not the way the ride 
will happen.  I plan to get on the bike and roughly set my course and speak with people on the way to find out about 
things to go and check out and find my way there using a bit of suggestive help from the Garmin.

Part of the fun of the ride is the preparation of the ride.  I'd mentioned in my earlier post that I had ambitions to 
take a certain amount of technology/digital stuff with me to record photos and transmit live GPS position updates to 
enable friends to track my progress online (probably with the help of Google Maps).  To add such complexity to the 
already involved task of riding a moto across the US might sound mad but I need a project to keep me busy until the ride.

****

### January 08, 2009 - Digital components for the NYC to SF ride.
Which breakable, non-weather proof, power hungry digital bits am I talking about?

 - Helmet with integrated Bluetooth. (as yet undecided manufacturer)
 - [Garmin Zumo 550 Motorcycle Navigator](http://www.garmin.com/zumo)
 - [Blackberry Curve](http://www.blackberry.com/blackberrycurve/)
 - [Tiny form factor PC - FitPC](http://www.fit-pc.com/new/about-fit-pc.html)
 - 2 mega pixel USB style camera.

The FitPC sounds crazy until you understand what it is to be used for and how compact and power light it is, so lets go 
through how all these pieces connect:
 - The helmet is to be paired via Bluetooth with the GPS in order to listen to music/radio and to provide annoying 
   direction "suggestions".
 - The GPS is to be connected via serial cable to the FitPC to provide latitude/longitude position data to be logged on 
   the FitPC.
 - The USB camera is to be mounted in a suitable weather proof enclosure and the FitPC will log snapshot images once 
   every X minutes.
 - The Blackberry is to be connected to the FitPC as a tethered modem to enable data transmission (when in service areas) 
   of position data and photo some limited photo snapshots when bandwidth over the Blackberry tethered modem permits.
 - The built-in WLAN will be configured to automatically join any available network (not that I expect to see many) and 
   "burst" as much data from the FitPC as possible.  I expect the tethered modem bandwidth to range from zero to limited 
   in many of the areas I'll travel so any opportunity to burst out a large chuck of data must be taken advantage of if 
   at all possible.

And then back here on nicholasdejong.com I simply create a simple bit of PHP that loads Google Maps along with my logged 
GPS data together with links to some snapshot images from the USB camera mounted out the front of the bike.  I'll add 
some capability for people to comment on the images and it should all be quite entertaining at your end.

I'm not worried (yet) about the power requirements since the later model KLR650's have larger alternators than they need 
and FitPC stock draws just 6W and can be configured to consume even less (see comments from the actual supplier below, 
thanks Irad!) when fitted with a solid state hard disk drive and video controller turned off - wow!

My real concern is that of vibration.  I'm surely going to observe Irad's comments (below) to really make sure my HDD is 
secure inside the FitPC to prevent it shaking around, my thought had been to place the FitPC into a purpose built shock 
absorbing little shelf/mount inside one of the sealed hard case side panniers - I'll find a way to make it work.

On the matter of vibration I purposely ordered my FitPC without a HDD so I could install a solid-state hdd that at least 
has a fighting chance of dealing with the constant vibration of a bike.  I purchased my SSD at the same time as the 
FitPC and was lucky to notice that within moments of pressing the online order button I'd purchased the wrong type of 
SSD (I'd purchased a SATA drive not an ATA).  Fortunately I was able to call and cancel the order right away before it 
entered their dispatch system.  Since then I've purchased a 32GB Transcend 2.5" Solid State IDE/ATA Disk which should 
be ample storage for my use.

In terms of sizing the SSD I've taken the following basic calculation -- a 28 day ride, probably 20 days total on the 
bike as I plan to stop here and there, 5 to 6 hours a day riding, 4500 miles from NYC to SF on my planned route means 
an average speed of 41 miles/hour.  I don't have a good sense of weather this is too fast or slow at this stage since my 
planned route avoids highways and the like, either way if it is too slow I can always join the highway for a few days 
to pick up the pace.  Why is all this important?  Well as you may have noticed I intend to take snapshot images from a 
camera on the front of the bike and so if the above numbers make sense I'll be on the bike for ~110 hours total which 
means if each image is 512Kb at I take an image every 10 seconds we are looking at ~20GB of images all up.

The resulting video should be interesting!

****

### January 15, 2009 - Motorcycle trip checklist

My natural concern is weight as it seems I'm already up to 20kgs of just "stuff" - sounds just crazy to me.

**Sleeping Gear (4.2 kgs)**
 - Sleeping Mat	 - 0.7 kgs - REI - REI Trekker 1.75 Self-Inflating Pad - Short
 - Small Tent - 3.5 kgs - kmart - Northwest Territory Dome Tent (this thing was cheap and one gets what one pays for - not 100% this is the tent for the job)

**Personal Gear (2 kgs)**
 - Tooth Brush
 - Toothpaste
 - Razor + replacements
 - First Aid Kit + Insect Repel
 - Eye drops + Lip Balm + Small Moisturizer
 - Metal Cup + Plate + fork + knife
 - Water Bottle 

**Tools (4kgs)**
 - Small Tool Kit + Leatherman
 - 2x Puncture Kits with refill gas
 - Hand pump
 - Type Pressure Gauge
 - Plastic Bags
 - Zip Ties (good strong ones)
 - Torch (LED self recharge type)
 - Recharge Battery Pack (already have, but heavy!!)

**Clothes (5kgs)**
 - Normal Shoes (Lite)
 - Undies / Socks
 - Spare Tee Shirts
 - Swimmers
 - Sunglasses
 - Quick Dry Towel (Car Sham Type)

**Other**
 - Photocopies of documents

While putting this list together I came by some other checklists for which I'll have to go back and compare my check 
list with their check list to see what I've forgotten and what I can get rid of. 

Other check lists:
 - [http://micapeak.com/checklists/](http://micapeak.com/checklists/)
 - [http://wetleather.com/reference/camping.html](http://wetleather.com/reference/camping.html)

****

### April 21, 2009 - The first real ride

I took the KLR out for its first real ride this weekend up to [Pine Plains](http://maps.google.com/maps?f=q&source=s_q&hl=en&q=Pine+Plains,+New+York&sll=37.0625,-95.677068&sspn=52.637906,81.210938&ie=UTF8&cd=1&geocode=FRWPgAIdZxic-w&split=0&z=14&iwloc=A)
which taught me a thing or two along the way.  First of all, I need to sort out a power supply circuit for my 
accessories.  My GPS ran out of battery power within the first 60 minutes, not at all surprising and I was fully 
expecting it but it really drove home for me how lost I am without it.

I found myself in some side town in New Jersy pulling off the fairings to get at the battery to keep the GPS running - as 
it turned out this was not the last time I'd be taking the fairing off the bike.

While sitting at a servo looking at my bike I noticed an oil leak.  This was really quite alarming as the bike only 
has ~2500 miles and this was my first decent ride.  Immediately I started thinking I'd purchased a handful of trouble 
with this second hand bike.  As I investigated it appeared the oil was coming from a fairly high point on the bike next 
to the battery which led me to popping open the air box where I discovered it to be full of oil and the air filter soaked 
-- I quickly realized what was going on.

It seems the previous owner had seriously overfilled the oil causing the crankshaft and counterweight to splash oil up 
through the carburettor and through the air filter!!  I removed about a liter of oil the messy way through the oil sump 
plug after which the bike suddenly ran smoother and I could select neutral again which seemed to be a related side 
effect, excellent!

Since this weekend was the first good weather weekend all year in the lower NY area every one with a moto was out and 
about - and so when a sportsbike overtook me going up a mountain, I (tried) to give chase.... only to discover that one 
should not go chasing sportsbikes with a load on the back across a pair of panniers.  It turns out that my nice new 
panniers can get a slight side to side wobble to them which, when traveling a pace and laying over in a corner causes 
the bike to feel like she want to fishtail up the road -- I feel like I have to write on the blackboard "I will not 
chase sportsbikes up the mountain with loaded panniers on" -- Anyway I'm glad I found out about this.

I later made the ride back to NYC in the dark and made a new discovery - either I did not fill the tank to the brim at 
my last fuel stop or the side panniers are really causing me a lot of drag resistance since I hit the fuel reserve 
limit at ~190 miles but fortunately right out the front of a gas station.

Finally as I got back towards home, riding back down the building canyons on Lexington Ave at 10pm on a Saturday night 
was kinda cool.

****

### May 25, 2009 - NYC > Rhode Island. > Hamptons > Montauk > NYC
I took a good long ride this weekend to load everything onto the bike and try a few things out along the way.  I got up 
early on Saturday morning and was on the road by 6:00am.  I had wanted to get an early start so I could get some good 
photos from the new camera mount now attached to the front of the bike.

**NYC > Rhode Is.**  
Apart from being on the road early this journey was pretty uneventful.  For the first ~3 hours I was able to get photos 
out the front of the bike (one shot every 30 seconds) however once I got back to review them it's all rather boring 
shots of an interstate highway.  No surprise in that of course but it has got me thinking that I'll re-orient the 
camera such that shots are taken at a slight angle off the right-hand side of the bike.  I did experience the 
speed-wobble problem again that seems to be associated with the side panniers and had a moment of elevated heart beats 
as the wind blast from beside a large semi trailer caught me.

**Twisted Throttle BBQ**  
The reason for Rhode Island was the fact that an online company, [Twisted Throttle](http://www.twistedthrottle.com) that 
I'd purchased bits from some sent out an email stating they were having a BBQ.  When I arrived I realized just how early 
in the morning it was when I departed Manhattan since I was the first non-employee to arrive in the car park.  It was a 
great day and I met quite a few great people and bikes.  Of particular note was Roy and his VStrom with load of great 
enhancements all over the bike.  Roy has developed a most enviable component, that being his moto-office which is 
literally an "office" located inside a waterproof pelican case in which he has a laptop, power and a solar panel 
attached to the top.  In the afternoon I decided to participate in the "slow race" and got quite over zealous about the 
whole thing as I dropped my bike in the middle of the race quite to the amusement of onlookers.  Whooops!  No dramas, 
not even a scratch, just somewhat embarrassing.  While I was in the carpark chatting a guy by the name of Gerard gave 
me the idea to move my Givi backcase forward on the bike.  As it turns out this not only bought the weight in the bike 
further forward but also seems to have removed much of the speed-wobble effect I was getting which makes perfect sense 
in hindsight.  My guess is that the back case was getting "caught" in the air blast as it passed around me and would 
at certain speeds get into harmonic where the case would wobble.  It seems this wobble was then being picked up by the 
side panniers which then amplified the whole thing due to their weight and thus result in a rather unpleasant sensation 
from the backend of the bike.  Anyway, the problem here has been greatly reduced by bringing the backcase forward which 
I'm quite happy about.

**Rhode Is. > Hamptons**  
In the afternoon I rode down to New London to catch the ferry across to Orient Point and then across to the Bridge 
Hampton on Long Island.  My timing was perfect and I was on the ferry departing within 20 minutes of arriving.  Once you 
get to Orient Point you can do one of two things, go down to Riverhead and loop back up Long Island or cut across Shelter 
Island taking more short ferry rides.  I took the ferries but I reckon on a moto it would be quicker to ride down to 
Riverhead and back.

**Hamptons > Montauk > New York City**  
I stayed overnight in Bridge Hampton and in the morning took myself up to Montauk affectionately known as "The End" 
since it is the last place on the end of Long Island.  There's a lighthouse there so I paid my $8 climbed the lighthouse 
and got back on the road headed for the city.  The journey to NYC was a real pain with the traffic and being Memorial 
Day weekend it was probably twice as bad as usual but after wrestling with the traffic made it back to the city by 
Sunday afternoon.

![onamoto-2](/images/posts/2008-12-29/IMG_2927.JPG "onamoto-2")
![onamoto-3](/images/posts/2008-12-29/IMG_2989.JPG "onamoto-3")

