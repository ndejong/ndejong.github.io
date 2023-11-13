---
layout: post
title: Keybase.io Network Graphs
author: Nicholas de Jong
---

Recently I became interested in [Keybase.io](https://keybase.io) and really wanted to be able explore my network-graph 
using [Gephi](https://gephi.org/), so I wrote a quick tool to collect the data from Keybase; dump it into GraphML file;
then loaded it up in Gephi.  The results nicely highlight who-knows-who; the strengths and weaknesses in my own Keybase
network; and super connector users with many followers.

### Keybase
Keybase is an interesting project, and the circle-of-trust improvements their tooling provides is probably better than
anything else out there at the moment.  The obvious concern is whether they have a business model that provides 
sufficient value to people (or enterprises) that will make Keybase long-term viable.
 - [Keybase raises $10.8M](https://keybase.io/blog/2015-07-15/keybase-raises-series-a) 
 - [Keybase on Crunchbase](https://www.crunchbase.com/organization/keybase)


### Github project
 - [https://github.com/ndejong/keybase-network-graph](https://github.com/ndejong/keybase-network-graph)

### Command line
```shell
$ ./keybase-network-graph.py -h
usage: keybase-network-graph.py [-h] --uid <uid> [--depth <depth>]
                                [--path <path>] [--nograph]
Keybase Network Grapher

optional arguments:
  -h, --help       show this help message and exit
  --uid <uid>      Initial uid to start collecting data on, required.
  --depth <depth>  Maximum depth of user connections to collect data on,
                   default = 1
  --path <path>    Maximum depth of user connections to collect data down to,
                   default = /tmp/keybase-network-graph
  --nograph        Prevent GraphML generation.
```

### Visualizations in Gephi

![screenshot_101043.png](https://raw.githubusercontent.com/ndejong/keybase-network-graph/master/assets/screenshot_101043.png)

![screenshot_075321.png](https://raw.githubusercontent.com/ndejong/keybase-network-graph/master/assets/screenshot_075321.png)

![screenshot_074349.png](https://raw.githubusercontent.com/ndejong/keybase-network-graph/master/assets/screenshot_074349.png)

