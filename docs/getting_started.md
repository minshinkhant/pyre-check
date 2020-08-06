---
id: getting-started
title: Getting Started
sidebar_label: Getting Started
---

## Requirements
You need a working [Python 3.6 or later](https://www.python.org/getit/) environment to run Pyre. We highly recommend that you install [watchman](https://facebook.github.io/watchman/) to get the most out of Pyre but it's not strictly necessary.

On *MacOS* you can get everything with [homebrew](https://brew.sh/):
```bash
$ brew install python3 watchman
```
In *Ubuntu*, *Mint* and *Debian* use `apt-get`:
```bash
$ sudo apt-get install python3 python3-pip watchman
```
We tested Pyre on *Ubuntu 16.04 LTS*, *CentOS 7*, as well as *OSX 10.11* and later.

## Setting up a Project
We're starting by creating an empty project directory, setting up a virtual environment.

```bash
$ mkdir my_project && cd my_project
$ python3 -m venv ~/.venvs/venv
$ source ~/.venvs/venv/bin/activate
(venv) $ pip install pyre-check
```

We now need to tell Pyre what to check by running
```bash
(venv) $ pyre init
```
This command will set up a configuration for Pyre (`.pyre_configuration`) as well as watchman (`.watchmanconfig`) in your project's directory.

## Running Pyre

We are now ready to run Pyre:
```bash
(venv) $ echo "i: int = 'string'" > test.py
(venv) $ pyre
 ƛ Found 1 type error!
test.py:1:0 Incompatible variable type [9]: i is declared to have type `int` but is used as type `str`.
```
Note that the first invocation initializes Pyre's server that handles incremental updates and will be slower than subsequent invocations – you can easily see this by invoking `pyre` again and observe the same result instantaneously.