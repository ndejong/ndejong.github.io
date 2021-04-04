---
layout: post
title: Using FauxAPI for pfSense users and groups
author: Nicholas de Jong
---

Recently a pfSense FauxAPI request came in as an issue on Github that I wrote example code to address because the 
use case sounded like a a common enough request - Github user [@Jgerardopine](https://github.com/Jgerardopine) spoke of 
wanting a programmatic method for creating (and managing) user accounts in pfSense and was looking to `pfsense_fauxapi` 
to address that requirement.  The example code can be found in the [`examples`](https://github.com/ndejong/pfsense_fauxapi_client_python/tree/master/examples)
section of the repo.

<br />

**From the [Github issue](https://github.com/ndejong/pfsense_fauxapi/issues/26) response**  

> This sounded like a common enough use-case that I created some example code that implements the following:-
> 
> - `get_users` - returns a dict of users on the system
> - `add_user` - adds a new user to the system
> - `manage_user` - manages users attributes such as password, sshkey, description and privileges
> - `remove_user` - removes a user by username
> - `get_groups` - returns a dict of groups on the system
> - `add_group` - creates a new local user group
> - `manage_group` - manages the description, privileges and users in a group
> - `remove_group` - removes a group by group name
> 
> You can review the code here:-
> https://github.com/ndejong/pfsense_fauxapi_client_python/blob/master/examples/usergroup-management.py
> 
> The thing to remember is that FauxAPI is a tool for interacting with the pfSense configuration file and as such you 
> sometimes need to do a bit of extra work here and there - in this case we need to increment the `nextuid` and `nextguid` 
> fields after adding users and groups - works just fine though

I ended up implementing a lot more functionality than the original question was asking because I wanted to know that
it was possible to add/remove/manage all aspects of a user and their privileges which then extended into doing
the same thing for user-groups.

More than this, it is a good demonstration of what the FauxAPI is and what it is not - it is a tool for interacting
with the pfSense configuration file and is it not a per action API that interacts with the entire pfSense system.  This 
is because the code behind pfSense does not separate code that renders the user-interface views from the code that 
handles system control features and functions which in turn means it is practically impossible to establish a nicely 
structured API that provides access and control to all the functionality within pfSense.  Being able to interact 
with the configuration file in a programmatic manner is however enormously useful and powerful. 
