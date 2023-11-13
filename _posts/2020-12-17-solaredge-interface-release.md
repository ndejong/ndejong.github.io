---
layout: post
title: SolarEdge API interface
author: Nicholas de Jong
---

Outside the usual realm of security-things, last week I published a SolarEdge Interface, a 
command-line and a Python module interface to interact with the SolarEdge API service that's a decent
improvement over the existing ones out there.

In short -
 * All (documented) SolarEdge API endpoints are implemented with multisite support for endpoints 
   that provide multisite queries.
 * Response data for all endpoints are available as a Python-dict structure; a Pandas-DataFrame or; 
   as raw-JSON.
 * The command-line interface output can be formatted as a CSV; as a Pandas style JSON structure or; 
   as plain-JSON.
 * Timestamps can be returned as datetime values with their respective site timezones applied. Doing 
   so is the default behaviour, however this can be disabled if required.
 * Configuration via environment variables or config file is possible, thus making it safer to manage 
   your API key value(s).

## Install
[![PyPi](https://img.shields.io/pypi/v/solaredge-interface.svg)](https://pypi.python.org/pypi/solaredge-interface/)
[![Python Versions](https://img.shields.io/pypi/pyversions/solaredge-interface.svg)](https://github.com/ndejong/solaredge-interface/)
[![Build Status](https://api.travis-ci.org/ndejong/solaredge-interface.svg?branch=master)](https://travis-ci.org/ndejong/solaredge-interface/)
[![Read the Docs](https://img.shields.io/readthedocs/solaredge-interface)](https://solaredge-interface.readthedocs.io)
![License](https://img.shields.io/github/license/ndejong/solaredge-interface.svg)

```shell
  pip install [--upgrade] solaredge-interface
```

## Documentation
* [solaredge-interface.readthedocs.io](https://solaredge-interface.readthedocs.io)

## Source
* Github - [github.com/ndejong/solaredge-interface](https://github.com/ndejong/solaredge-interface)

## Usage
```shell
Usage: solaredge-interface [OPTIONS] COMMAND [ARGS]...

  The solaredge-interface provides a command-line interface to interact with
  the Python SolarEdgeAPI module which itself calls the SolarEdge public API
  endpoints at https://monitoringapi.solaredge.com making it even easier to
  access your data from SolarEdge.

  Configuration can be achieved through command arguments, environment
  values or config file.

  Documentation available https://solaredge-interface.readthedocs.io

Options:
  -c, --config TEXT       Override default config ~/.solaredge-interface
  -f, --format TEXT       Output format; csv, json, pandas (default: json)
  -v, --verbose           Verbose logging messages (debug level).
  -q, --quiet             Quiet mode, with priority over --verbose
  -W, --disable-warnings  Disable Python warnings.
  --version               Show the version and exit.
  --help                  Show this message and exit.

Commands:
  accounts                     Get the accessible >sub< accounts.
  site_current_power_flow      Current power flow between all elements of...
  site_data_period             Sites(s) start_date and end_date of...
  site_details                 Get site details; name, location, status,...
  site_energy                  Site(s) energy measurements
  site_energy_details          Detailed site energy measurements from meters
  site_environmental_benefits  Environmental benefits based on site energy...
  site_equipment_change_log    Equipment component replacements ordered by...
  site_equipment_data          Get specific inverter data for a given...
  site_equipment_sensors       Sensors in the site and connections
  site_inventory               Inventory of SolarEdge equipment at the site
  site_meters                  Meter lifetime energy, metadata and...
  site_overview                Sites(s) overview data
  site_power                   Site(s) power measurements
  site_power_details           Detailed site power measurements from meters
  site_storage_data            Detailed storage information from batteries
  site_time_frame_energy       Site(s) total energy produced for a given...
  sites                        Get the list of accessible sites
  version_current              Current version in <major.minor.revision>...
  version_supported            Supported version numbers in...
```