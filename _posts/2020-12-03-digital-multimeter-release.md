---
layout: post
title: Digital Multimeter interface
author: Nicholas de Jong
---

Wrote a digital multimeter CLI tool (and Python module) to read an old Digitech QM1538 
multimeter sold by Jaycar, Australia.  This was a weekend-project that started with a 
scratchy old data-sheet that described the serial-protocol used by this thing.  I'd not 
written a serial-protocol decoder before and the tool would make my digital-multimeter 
usable via Linux and accessible remotely via SSH which is what I really wanted in this 
case.

It turns out that the underlying chipset (Fortune FS9721) used by this multimeter is rather 
common among other digital multimeters too, so the CLI and accompanying Python module 
should work for a whole host of other digital multimeters out there - 
 - Digitech - QM1538
 - Digitek - DT4000ZC
 - PCE - PCEDM32
 - Tecpel - DMM8062
 - TekPower - TP4000ZC
 - UniTrend - UT30A
 - UniTrend - UT30E
 - UniTrend - UT60E
 - Voltcraft - VC820
 - Voltcraft - VC840

The Python module is written to accommodate new digital-multimeter protocols.  If you 
happen to implement another digital-multimeter protocol please do send a merge 
request - happy days.

## Install
[![PyPi](https://img.shields.io/pypi/v/digital-multimeter.svg)](https://pypi.python.org/pypi/digital-multimeter/)
[![Python Versions](https://img.shields.io/pypi/pyversions/digital-multimeter.svg)](https://github.com/ndejong/digital-multimeter/)
[![Read the Docs](https://img.shields.io/readthedocs/digital-multimeter)](https://digital-multimeter.readthedocs.io)
![License](https://img.shields.io/github/license/ndejong/digital-multimeter.svg)

```shell
pip install [--upgrade] digital-multimeter
```

## Documentation
* [digital-multimeter.readthedocs.io](https://digital-multimeter.readthedocs.io)

## Source
* [github.com/ndejong/digital-multimeter](https://github.com/ndejong/digital-multimeter)

## Usage
```shell
Usage: dmm [OPTIONS] COMMAND [ARGS]...

  Digital multimeter CLI tool utilizing the Python3 DigitalMultimeter module.

  Configuration can be achieved through command arguments, environment values
  or config file.

  Documentation available https://digital-multimeter.readthedocs.io

Options:
  -q, --quiet             Quiet mode; priority over --verbose
  -v, --verbose           Verbose logging; debug level.
  -W, --disable-warnings  Disable Python warnings.
  --version               Show the version and exit.
  --help                  Show this message and exit.

Commands:
  models  Provides a list of the supported digital multimeter models
  read    Read the digital multimeter and output data in various formats
```