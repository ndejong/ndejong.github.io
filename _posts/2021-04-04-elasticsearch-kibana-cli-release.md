---
layout: post
title: Elasticsearch Kibana CLI (eskbcli) release v0.3.1
author: Nicholas de Jong
---

Published another CLI tool I've had in my back-pocket for a while and frequently rely on when working 
threat-response / threat-management cases where direct access to ElasticSearch is not possible.  This
situation comes up a little more often than you'd think in security-operations situations because the
ElasticSearch backend often gets tucked away and made out-of-reach.

In short -

ElasticSearch Kibana CLI (`eskbcli`) provides a shell interface to query an ElasticSearch backend via 
the Kibana frontend which is useful in situations where the ElasticSearch backend is not otherwise 
accessible.

ElasticSearch Kibana CLI makes it possible to copy-paste query expressions directly from the Kibana 
user-interface and then locally access very large sets of result data.  This makes `eskbcli` useful 
in SecOps situations where the ability to rapidly move from a Kibana query to raw data is valued.

Configuration options are available to adjust http-headers so-as-to enable access to Kibana in 
situations that require complex user-authentication such as when Kibana exists behind an OAuth 
reverse proxy or other session-based authentication arrangements.

### Install
```bash
user@computer:~$ pip install elasticsearch-kibana-cli
```

Read the full documentation with usage details and examples - [elasticsearch-kibana-cli.readthedocs.io](https://elasticsearch-kibana-cli.readthedocs.io).

## Project
* Github - [github.com/ndejong/elasticsearch_kibana_cli](https://github.com/ndejong/elasticsearch_kibana_cli)
* PyPI - [pypi.python.org/pypi/elasticsearch-kibana-cli](https://pypi.python.org/pypi/elasticsearch-kibana-cli/)
* TravisCI - [travis-ci.org/github/ndejong/elasticsearch_kibana_cli](https://travis-ci.org/github/ndejong/elasticsearch_kibana_cli)
* ReadTheDocs - [elasticsearch-kibana-cli.readthedocs.io](https://elasticsearch-kibana-cli.readthedocs.io)
