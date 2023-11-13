---
layout: post
title: Python client for pfSense FauxAPI 
author: Nicholas de Jong
---

For longest time I'd been meaning to roll a PyPi package for the Python client interface to FauxAPI, and it is now a
thing - it also closes the long open issue [#22](https://github.com/ndejong/pfsense_fauxapi/issues/22) asking about PyPi from way back.

### pfsense-fauxapi
[![PyPi](https://img.shields.io/pypi/v/pfsense-fauxapi.svg)](https://pypi.org/project/pfsense-fauxapi/) [![Build Status](https://travis-ci.org/ndejong/pfsense_fauxapi_client_python.svg?branch=master)](https://travis-ci.org/ndejong/pfsense_fauxapi_client_python)

Install it using pip:-
```shell
  pip install pfsense-fauxapi
```

### Github project
 - [github.com/ndejong/pfsense_fauxapi_client_python](https://github.com/ndejong/pfsense_fauxapi_client_python)

### Command Line
Additionally this pip-package provides a command-line interface to work with FauxAPI
```shell
usage: fauxapi [-h] [--host [host]] [--apikey [key]] [--apisecret [secret]]
               [--verified-ssl] [--debug]
               [function] [[function] ...] [[function-args]]

FauxAPI

optional arguments:
  -h, --help            show this help message and exit

Call:
  --host [host]         Host address of the target pfSense host with the
                        PfsenseFauxapi package installed.
  --apikey [key]        FauxAPI apikey value - alternatively via the
                        FAUXAPI_APIKEY environment variable.
  --apisecret [secret]  FauxAPI apisecret value - alternatively via the
                        FAUXAPI_APIKEY environment variable.
  --verified-ssl        Enable SSL certificate checks - default does NOT check
                        SSL certificates.
  --debug               Enable debug response from the remote FauxAPI -
                        helpful in tracking down issues.
  [function]            The FauxAPI function being called
  [function-args]       Arguments to the function, space separated
```

Command line example, using environment variables to pass the ```FAUXAPI_APIKEY``` and ```FAUXAPI_APIKEY``` credentials.
```shell
$ fauxapi --host 192.168.1.200 gateway_status | jq .
{
  "callid": "5c8d0f7361cba",
  "action": "gateway_status",
  "message": "ok",
  "data": {
    "gateway_status": {
      "10.11.12.1": {
        "monitorip": "10.10.10.1",
        "srcip": "10.10.10.200",
        "name": "WAN_DHCP",
        "delay": "0.422ms",
        "stddev": "0.073ms",
        "loss": "0.0%",
        "status": "none"
      }
    }
  }
}
```

### Package Testing
Tests for (almost) all client-side function calls are implemented with mocked API response data
you can check them with pytest
```shell
  python setup.py test
```

Packages are tested via Travis
[travis-ci.org/ndejong/pfsense_fauxapi_client_python](https://travis-ci.org/ndejong/pfsense_fauxapi_client_python)

### Package Build
Should you need/want to build the package from source
```shell
# obtain the source material
git clone https://github.com/ndejong/pfsense_fauxapi_client_python.git
cd pfsense_fauxapi_client_python

# build the package
python setup.py sdist bdist_wheel

# install the package from the .whl file in the dist path 
pip install dist/pfsense*.whl
```
