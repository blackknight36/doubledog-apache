<!--
# This file is part of the doubledog-apache Puppet module.
# Copyright 2018 John Florian
# SPDX-License-Identifier: GPL-3.0-or-later
-->

# apache

#### Table of Contents

1. [Description](#description)
1. [Setup - The basics of getting started with apache](#setup)
    * [What apache affects](#what-apache-affects)
    * [Setup requirements](#setup-requirements)
    * [Beginning with apache](#beginning-with-apache)
1. [Usage - Configuration options and additional functionality](#usage)
1. [Reference - An under-the-hood peek at what the module is doing and how](#reference)
    * [Classes](#classes)
    * [Defined types](#defined-types)
1. [Limitations - OS compatibility, etc.](#limitations)
1. [Development - Guide for contributing to the module](#development)

## Description

This module lets you manage the Apache httpd web server.

## Setup

### What apache Affects

### Setup Requirements

### Beginning with apache

## Usage

## Reference

**Classes:**

* [apache](#apache-class)
* [apache::package](#apachepackage-class)
* [apache::service](#apacheservice-class)

**Defined types:**


### Classes

#### apache class

This class manages the primary configuration, SELinux settings and firewall.  This also implies management of the [minimal packaging](#apachepackage-class) and the [service](#apacheservice-class).

##### `anon_write`
Should SELinux allow httpd to modify public files used for public file transfer services?  Either `true` or `false` (default).

##### `log_level`
Limits the level of messages logged to the `error_log`.  Valid values are: `debug`, `info`, `notice`, `warn`, `error`, `crit`, `alert`, `emerg`.  The default is `warn`.

##### `manage_firewall`
If `true`, open the HTTP port on the firewall.  Otherwise the firewall is left unaffected.  Defaults to `true`.

##### `network_connect`
Should SELinux allow httpd scripts and modules to connect to the network using TCP?  Either `true` or `false` (default).

##### `network_connect_db`
Should SELinux allow httpd scripts and modules to connect to databases over the network?  Either `true` or `false` (default).

##### `use_nfs`
Should SELinux allow serving content reached via NFS?  Either `true` or `false` (default).


#### apache::package class

This class manages packages needed for a minimal installation.

##### `names`
An array of package names needed for a minimal installation.  The default should be correct for supported platforms.


#### apache::service class

This class manages the service itself.

##### `daemon`
The service name of the httpd daemon.  The default should be correct for supported platforms.

##### `enable`
Instance is to be started at boot.  Either `true` (default) or `false`.

##### `ensure`
Instance is to be `running` (default) or `stopped`.  Alternatively, a Boolean value may also be used with `true` equivalent to `running` and `false` equivalent to `stopped`.


### Defined types


## Limitations

Tested on modern Fedora and CentOS releases, but likely to work on any Red Hat variant.  Adaptations for other operating systems should be trivial as this module follows the data-in-module paradigm.  See `data/common.yaml` for the most likely obstructions.  If "one size can't fit all", the value should be moved from `data/common.yaml` to `data/os/%{facts.os.name}.yaml` instead.  See `hiera.yaml` for how this is handled.

This should be compatible with Puppet 3.x and is being used with Puppet 4.x as well.

## Development

Contributions are welcome via pull requests.  All code should generally be compliant with puppet-lint.