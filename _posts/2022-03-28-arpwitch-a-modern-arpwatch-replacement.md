---
layout: post
title: Arpwitch - a modern arpwatch replacement
author: Nicholas de Jong
---

**Arpwitch** is a modern arpwatch replacement with JSON formatted outputs and 
easy options to trigger exec commands when network changes are observed.

* outputs are JSON which makes it nice-and-easy to pair with other tools
* easy triggers to **--exec** system commands when new network hosts are seen.

Since performing an **nmap** on new network hosts is a useful thing, there is also
a built-in call to nmap that will invoke nmap with relatively mild but
useful settings - you can easily fall back to a regular **--exec** if you need to
do something more advanced.

## Install
[![PyPi](https://img.shields.io/pypi/v/arpwitch.svg)](https://pypi.python.org/pypi/arpwitch/)
[![Python Versions](https://img.shields.io/pypi/pyversions/arpwitch.svg)](https://github.com/ndejong/arpwitch/)
[![Build Tests](https://github.com/ndejong/arpwitch/actions/workflows/build-tests.yml/badge.svg)](https://github.com/ndejong/arpwitch/actions/workflows/build-tests.yml)
[![Read the Docs](https://img.shields.io/readthedocs/arpwitch)](https://arpwitch.readthedocs.io)
![License](https://img.shields.io/github/license/ndejong/arpwitch.svg)

```bash
pip install [--upgrade] arpwitch
```

## Example
```shell
arpwitch --debug --nmap --datafile /tmp/arpwitch.dat | jq .
```
The example above, watches for new network hosts; invokes an nmap scan
on them when they are discovered and saves results in XML format; saves
the arpwitch datafile to file `/tmp/arpwitch.dat` (it's JSON); pipes 
the output through JQ to make it look pretty.

NB: arpwitch requires root/sudo access in order to packet-capture from the 
network interface(s) - the rather awesome [scapy](https://scapy.net/) Python 
library is used for packet capture.

## Documentation
Plenty more documentation and examples here -
* [arpwitch.readthedocs.io/en/latest](https://arpwitch.readthedocs.io/en/latest/)

## Source
Have moved this repo from where I originally published it under verbnetworks (the laboratory) 
 * [github.com/ndejong/arpwitch](https://github.com/ndejong/arpwitch)

## Python Package
 * [pypi.org/project/arpwitch](https://pypi.org/project/arpwitch/)


## Usage 
```shell
usage: arpwitch [-h] [-f <datafile>] [-i <seconds>] [-req | -noreq | -allreq]
                [-rep | -norep | -allrep] [-e <command>] [-n] [-u <user>]
                [-q <address>] [-v] [-w] [-d]

A modern arpwatch replacement with JSON formatted outputs and easy options to
execute commands when network changes are observed.

optional arguments:
  -h, --help            show this help message and exit
  -req, --new-request   Select ARP request packet events that include new
                        ip/hw addresses not yet observed (DEFAULT).
  -noreq, --no-request  Ignore all ARP request packet events.
  -allreq, --all-request
                        Select all ARP request packet events regardless if
                        addresses have been previously observed.
  -rep, --new-reply     Select only reply packet events that include new ip/hw
                        addresses not yet observed (DEFAULT).
  -norep, --no-reply    Ignore all ARP reply packet events.
  -allrep, --all-reply  Select all ARP reply packet events regardless if the
                        addresses have been previously observed.

datafile arguments:
  -f <datafile>, --datafile <datafile>
                        The arpwitch datafile where ARP event data is stored
                        as a JSON formatted file (REQUIRED). The datafile is
                        also easy to manually query and inspect with external
                        tools such as `jq`
  -i <seconds>, --interval <seconds>
                        Interval seconds between writing to the datafile
                        (DEFAULT: 30)

ARP event command execution arguments:
  The following exec command substitutions are available: {IP}=ipv4-address,
  {HW}=hardware-address, {TS}=timestamp-utc, {ts}=timestamp-utc-short

  -e <command>, --exec <command>
                        Command line to exec on selected ARP events. Commands
                        are run async
  -n, --nmap            A hard coded convenience --exec that causes nmap to be
                        run against the IPv4 target with nmap-XML formatted
                        output written to the current-working-directory. This
                        option cannot be used in conjunction with --exec.
  -u <user>, --user <user>
                        User to exec commands with, if not set this will be
                        the same user context as arpwitch.

run-mode arguments:
  Switches that invoke run-modes other than ARP capture.

  -q <address>, --query <address>
                        Query the <datafile> for an IPv4 or HW address and
                        return results in JSON formatted output and exit.
  -v, --version         Return the arpwitch version and exit.
  -w, --witch           Supply one witch to <stdout> and exit.
  -d, --debug           Debug messages to stdout.

```
