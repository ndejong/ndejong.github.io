---
layout: post
title: Azure-cli via Docker and .bash_aliases entry
author: Nicholas de Jong
---

If you're a little cautious around [everything from Microsoft](https://krebsonsecurity.com/?s=microsoft+patch) 
then using their Docker container is a decent approach to manage those concerns.  Unfortunately,
as tends to be the case with a lot of Microsoft [documentation](https://docs.microsoft.com/en-us/cli/azure/run-azure-cli-docker),
it's verbose and long but is somehow missing details that make things real-world useful.

Fixing that then -

Use the following **.bash_aliases** entry to wrap the **az** alias-command with something that
invokes a Docker container locally.

```bash
alias az="docker run --rm --interactive --log-driver=none --attach stdin --attach stdout --attach stderr --volume ${HOME}/.azure:/root/.azure:rw --volume ${HOME}/.ssh:/root.ssh mcr.microsoft.com/azure-cli az"
```

The above uses long-form docker args to make it a little easier to understand what it all 
means.

Breaking that down into parts -
* **docker run** -- causes the container from **mcr.microsoft.com/azure-cli** to be run with 
  the command **az** (at the end of the command line)
* **--rm** -- causes the container to be removed after the command has completed.
* **--interactive** -- keeps the Docker console connection open for stdin/stdout/stderr
* **--log-driver=none** -- prevent otherwise hidden container log messages
* **--attach** -- attach each of stdin, stdout and stderr; which is important for az since 
  stderr and stdout otherwise gets collapsed onto one-another making it not-possible to pipe 
  output in your local environment, such as when piping through **jq** (further detail below)
* **--volume ${HOME}/.azure:/root/.azure** -- mount your ~/.azure into the Docker container 
  so the Azure authentication is persistent between docker invocations; you may want to 
  consider placing this mount on a separately encrypted mount.
* **--volume ${HOME}/.ssh:/root.ssh** -- mount your ~/.ssh path into the Docker container. 

With this alias in-place you'll be invoking a (local) Docker container to handle the "dirty" 
Microsoft stuff.

Further notes:-
* be sure to use **--attach** to pass through stdin, stdout and stderr else you will have 
  problems when piping output into something like **jq** - the issue is that the azure-cli 
  tooling writes command progress/status output to the terminal in a way that gets hidden 
  by using line-feed characters - if you redirect the output from docker to file or string and 
  then view that string you may miss the fact that there are line(s) not visible - if you strip
  the line-feeds by piping **| tr -d '\r'** you'll then uncover the azure-cli status messages
  at the head of string :(  that's the long story.
