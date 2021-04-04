---
layout: post
title: SolarEdge Interface release v0.3.2
author: Nicholas de Jong
---

Last week I published my SolarEdge Interface, a command-line and a Python module interface to interact with 
the SolarEdge API service.

In short -
 * All (documented) SolarEdge API endpoints are implemented with multisite support for endpoints that provide multisite queries.
 * Response data for all endpoints are available as a Python-dict structure; a Pandas-DataFrame or; as raw-JSON.
 * The command-line interface output can be formatted as a CSV; as a Pandas style JSON structure or; as plain-JSON.
 * Timestamps can be returned as datetime values with their respective site timezones applied. Doing so is the default behaviour, however this can be disabled if required.
 * Configuration via environment variables or config file is possible, thus making it safer to manage your API key value(s).

### Install
```bash
user@computer:~$ pip install solaredge-interface
```

Read the full documentation with usage details and examples at - [solaredge-interface.readthedocs.io](https://solaredge-interface.readthedocs.io)

### Project
 * Github - [github.com/ndejong/solaredge-interface](https://github.com/ndejong/solaredge-interface)
 * PyPI - [pypi.python.org/pypi/solaredge-interface](https://pypi.python.org/pypi/solaredge-interface)
 * TravisCI - [travis-ci.org/github/ndejong/solaredge-interface](https://travis-ci.org/github/ndejong/solaredge-interface)
 * ReadTheDocs - [solaredge-interface.readthedocs.io](https://solaredge-interface.readthedocs.io)
