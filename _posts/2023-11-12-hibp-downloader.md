---
layout: post
title: Hibp-downloader - download api.pwnedpasswords.com fast 
author: Nicholas de Jong
---

**hibp-downloader** is a CLI tool to efficiently download a local copy of the pwned 
password hash data from the very awesome HIBP pwned passwords api-endpoint using all 
the good bits; multiprocessing, async-processes, local-caching, content-etags and 
http2-connection pooling to make things as fast as is Pythonly possible.

## Features
 - Easily resume interrupted download operations into a --data-path without re-clobbering api-source.
 - Only download hash-prefix content blocks when the source content has changed (via content ETAG values); thus making it easy to periodically re-sync when needed.
 - Ability to directly query for compromised password values from the data in-place; efficient enough to attach a service with reasonable loads.
 - Ability to generate a single text file with in-order pwned password hash values, similar to PwnedPasswordsDownloader from the HIBP team.
 - Per prefix file metadata in JSON format for easy data reuse by other tooling if required.

## Usage 
![screenshot-help](/images/posts/2023-11-12/screenshot-help.png "screenshot-help")

## Install
[![PyPi](https://img.shields.io/pypi/v/hibp-downloader.svg)](https://pypi.python.org/pypi/hibp-downloader/)
[![Python Versions](https://img.shields.io/pypi/pyversions/hibp-downloader.svg)](https://github.com/threatpatrols/hibp-downloader/)
[![Build Tests](https://github.com/threatpatrols/hibp-downloader/actions/workflows/build-tests.yml/badge.svg)](https://github.com/threatpatrols/hibp-downloader/actions/workflows/build-tests.yml)
[![Read the Docs](https://img.shields.io/readthedocs/hibp-downloader)](https://hibp-downloader.readthedocs.io)
![License](https://img.shields.io/github/license/threatpatrols/hibp-downloader.svg)

```bash
pip install [--upgrade] hibp-downloader
```

## Documentation
Plenty more documentation and examples here -
* [hibp-downloader.readthedocs.io](https://hibp-downloader.readthedocs.io/en/latest/)

## Source
 * [github.com/threatpatrols/hibp-downloader](https://github.com/threatpatrols/hibp-downloader)

## Python Package
 * [https://pypi.org/project/hibp-downloader/](https://pypi.org/project/hibp-downloader/)
