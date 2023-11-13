---
layout: post
title: Env-Alias environment helper utility
author: Nicholas de Jong
---

Env-Alias is a helper utility to create shell alias commands that easily set collections of 
environment variables often with secret values from a variety of data-sources and data-formats.

Typically this tool is invoked via an entry in `.bash_aliases` with an entry in the form
```shell
  eval $(env-alias my-alias-name ~/path-to/my-alias-name-config-file.yml)
```

Where this example would establish a shell alias command for the alias **my-alias-name** that 
then invokes the env-alias-generator with configuration from **~/path-to/my-alias-name-config-file.yml**

That all might sound quirky, however the mechanism is enormously useful in working with large sets of 
environment variables from encrypted or otherwise secured data-sources which means an environment 
configuration can be easily committed to source control without the secret values.

## Features
* Data sources: local-file, http-remote, exec-stdout or directly-set
* Source file formats: `text`, `ini`, `json`, `yaml`
* Select using jq-style selectors, xpath selectors or line-numbers
* Reference other env values within configuration
* Content-Type detection for http-remote data-sources to automatically assign appropriate parser
* Run exec helper commands without content assignment for creating setups 
* Logs output to STDERR
* Easy installation using PyPI `pip`
* Plenty of documentation and examples - [https://env-alias.readthedocs.io](https://env-alias.readthedocs.io)

## Install
[![PyPi](https://img.shields.io/pypi/v/env-alias.svg)](https://pypi.python.org/pypi/env-alias/)
[![Python Versions](https://img.shields.io/pypi/pyversions/env-alias.svg)](https://github.com/ndejong/env-alias/)
[![Build Status](https://github.com/ndejong/env-alias/actions/workflows/build-tests.yml/badge.svg)](https://github.com/ndejong/env-alias/actions/workflows/build-tests.yml)
[![Read the Docs](https://img.shields.io/readthedocs/env-alias)](https://env-alias.readthedocs.io)
![License](https://img.shields.io/github/license/ndejong/env-alias.svg)
```shell
pip install [--upgrade] env-alias
```

## Documentation
Read the documentation, there really is a lot of awesome things to do with env-alias
* [env-alias.readthedocs.io](https://env-alias.readthedocs.io)

## Source
* [github.com/ndejong/env-alias](https://github.com/ndejong/env-alias)

