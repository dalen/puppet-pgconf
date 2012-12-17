Pgconf defined type
===================

This module allows to manage entries in Postgresql's configuration file
(postgresql.conf).

It provides a `pgconf` defined type, and a provider based on ParsedFile. It was
originally part of
[camptocamp/puppet-postgresql](https://github.com/camptocamp/puppet-postgresql)
and has been split out in an independent module to allow other postgresql
modules to benefit from it.

Basic usage
-----------

```Puppet
pgconf { 'listen_addresses':
  ensure => present,
  value  => 'localhost',
  target => '/etc/postgresql/9.1/main/postgresql.conf',
}
```

Limitations
-----------

It does not take care of restarting/reloading postgresql after changing the
configuration file. It does not increase sysctl values required before changing
some of postgresql's settings.


What about Augeas ?
-------------------

Keys in postgresql.conf are case-insensitive, which is something augeas doesn't
support before (yet unreleased) version 1.0. This module will be abandoned once
postgresql.conf can be properly managed by augeas.

