---
layout: post
title: Env-Alias release v0.1.6
author: Nicholas de Jong
---

Env-Alias is a helper utility to create shell alias commands that easily set collections of environment variables 
often with secret values from a variety of data-sources and data-formats.

Typically this tool is invoked via an entry in `.bash_aliases` with an entry in the form
```bash
eval $(env-alias my-alias-name ~/path-to/my-alias-name-config-file.yml)
```

Where this example would establish a shell alias command for the alias `my-alias-name` that then invokes the 
env-alias-generator with configuration from `~/path-to/my-alias-name-config-file.yml`

That all might sound quirky, however the mechanism is enormously useful in working with large sets of 
environment variables from encrypted or otherwise secured data-sources which means an environment 
configuration can be easily committed to source control without the secret values.

### Features
* Data sources: local-file, http-remote, exec-stdout or directly-set
* Source file formats: `text`, `ini`, `json`, `yaml`
* Select using jq-style selectors, xpath selectors or line-numbers
* Reference other env values within configuration
* Content-Type detection for http-remote data-sources to automatically assign appropriate parser
* Run exec helper commands without content assignment for creating setups 
* Logs output to STDERR
* Easy installation using PyPI `pip`
* Plenty of documentation and examples - [https://env-alias.readthedocs.io](https://env-alias.readthedocs.io)

### Install
```bash
pip install env-alias
```

### Project
 * Github - [github.com/ndejong/env-alias](https://github.com/ndejong/env-alias)
 * PyPI - [pypi.python.org/pypi/env-alias](https://pypi.python.org/pypi/env-alias)
 * TravisCI - [travis-ci.org/github/ndejong/env-alias](https://travis-ci.org/github/ndejong/env-alias)
* ReadTheDocs - [env-alias.readthedocs.io](https://env-alias.readthedocs.io)
