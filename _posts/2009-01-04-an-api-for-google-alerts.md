---
layout: post
title: An API for Google Alerts
author: Nicholas de Jong
excerpt: <p>Google recently enhanced such that it is possible to obtain RSS feeds of canned searches.  This is enormously useful but there is no API that enables one to programmatically list, add and remove items to their set of Google Alerts.  So partly because it's too cold outside to do anything and partly because this seems like useful functionality I spent a few hours today writing a PHP class that implements an API to Google Alerts.</p>
---

### July 10, 2018
I originally wrote this ~10 years ago.  It was a chance thing that caused a good deal of interest at the time, the original
code is [available on my Github](https://github.com/ndejong/google_alert_api) which is unlikely to work anymore, because
much has changed with Google and the way the Google Alert service works.

****

### January 4, 2009
Google recently enhanced [Google Alerts](http://www.google.com/alerts) such that it is possible to obtain RSS feeds of 
canned searches.  This is enormously useful but there is no API that enables one to programmatically list, add and 
remove items to their set of Google Alerts.  So partly because it's too cold outside to do anything and partly because 
this seems like useful functionality I spent a few hours today writing a PHP class that implements an API to Google Alerts.

The only required input parameters for this class are the Google account username and password.  Reasonable defaults are 
chosen for all other parameters, which can be adjusted if needed.

### GoogleAlertApiClass()
 - **username**   = [required] google account username
 - **password**   = [required] corrosponding google account password
 - **cookiefile** = location of an alternate cookie file to be used.  The cookie file manages and maintains the logged in session state.
 - **useragent**  = adjust the user agent presented if you feel the need.
 - **logtypes**   = an array containing the message types to be logged.  Valid values are 'FATAL','ERROR','WARNING','INFO','DEBUG'.
 - **logterm**    = a bool value that determines if log messages should be sent to terminal.

### Functions available:
 - **alertList()** -- Can be caled once a GoogleAlertApiClass has been created.  Returns an array of alert terms and their respective RSS feed URLs.
 - **alertAdd(string[TERM])** -- adds a new google alert.  Returns 1 of sucess or 0 on failure.
 - **alertRemove(string[TERM])** -- removes a google alert term. Returns 1 of sucess or 0 on failure.
 - **alertEdit(string[OLD_TERM], string[NEW_TERM])** -- shortcut function, simply calls alertRemove and alertAdd on their respective terms. Returns 1.
 - **log(BOOL)** -- when input is FALSE, returns an array of the last 10 enabled log type messages.  When input is FALSE returns as a string.
