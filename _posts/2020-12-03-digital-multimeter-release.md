---
layout: post
title: Digital Multimeter release v0.1.6
author: Nicholas de Jong
---

Wrote a digital multimeter CLI tool (and Python module) to read an old Digitech QM1538 multimeter sold by 
Jaycar, Australia.  This was a weekend-project that started with a scratchy old data-sheet that described 
the serial-protocol used by this thing.  I'd not written a serial-protocol decoder before and the tool
would make my digital-multimeter usable via Linux and accessible remotely via SSH which is what I really
wanted in this case.

It turns out that the underlying chipset (Fortune FS9721) used by this multimeter is rather common among 
other digital multimeters too, so the CLI and accompanying Python module should work for a whole host of 
other digital multimeters out there - 
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

The Python module is written to accommodate new digital-multimeter protocols.  If you happen to 
implement another digital-multimeter protocol please do send a merge request - happy days.

Wrote some pretty documentation too - [digital-multimeter.readthedocs.io](https://digital-multimeter.readthedocs.io/en/latest/)

### Installation
```shell
user@computer:~$ pip install digital-multimeter
```

### Project
* Github - [github.com/ndejong/digital-multimeter](https://github.com/ndejong/digital-multimeter)
* PyPI - [pypi.python.org/pypi/digital-multimeter](https://pypi.python.org/pypi/digital-multimeter/)
* TravisCI - [travis-ci.org/github/ndejong/digital-multimeter](https://travis-ci.org/github/ndejong/digital-multimeter)
* ReadTheDocs - [digital-multimeter.readthedocs.io](https://digital-multimeter.readthedocs.io)
