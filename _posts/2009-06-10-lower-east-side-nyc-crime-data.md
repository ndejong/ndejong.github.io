---
layout: post
title: Lower East Side New York City Crime Data
author: Nicholas de Jong
---

An API end point that returns crime data for cities in the United States.  This post has been updated using command-
line tools rather than PHP code, however the original end-point is still alive and well with up-to-date data.

```bash
curl -s 'https://spotcrime.com/cache/main/manhattan-lower-east-side.js' | jq .

{
  "createdate": "2018-07-12 22:03",
  "crimeList": [
    {
      "cdid": "110655834",
      "calc_date": "07/08/2018",
      "calc_time": "02:00 PM",
      "clatitude": "40.71653970000000",
      "clongitude": "-73.99992990000000",
      "cdescription": "Felony Assault. Peace Officer",
      "caddress": "77A BAXTER ST",
      "ccity": "Manhattan",
      "cid": "30",
      "cname": "Assault",
      "icon": "30",
      "reference": "",
      "reference_id": "",
      "type": "C",
      "sid": "110655834-cd20da3e87ca18fe85b86fd7f9c11a5f",
      "user": ""
    },
    {
      "cdid": "110651450",
      "calc_date": "07/08/2018",
      "calc_time": "07:00 AM",
      "clatitude": "40.71878000000000",
      "clongitude": "-73.99570000000000",
      "cdescription": "Misd. Assault. Assault 3",
      "caddress": "00 BLOCK OF ELIZABETH ST",
      "ccity": "Manhattan",
      "cid": "30",
      "cname": "Assault",
      "icon": "30",
      "reference": "",
      "reference_id": "",
      "type": "C",
      "sid": "110651450-07d627bde10fbc539ad79e0aef193474",
      "user": ""
    },
...

``` 
