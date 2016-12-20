ntp
===

A simple role to install and configure the latest ntpd with remote ntp server
pools.

For CentOS, Redhat, Debian or Ubuntu

Tested using Ansible 2.1.2 on:

CentOS 7
Debian Jessie
Ubuntu Trusty

Requirements
------------

Ansible 2+

Role Variables
--------------

```yml
# Timezone of your machine
ntp_timezone: "UTC"
# List of NTP servers. This must contain at least 1 server
ntp_servers:
  - 0.uk.pool.ntp.org iburst
  - 1.uk.pool.ntp.org iburst
  - 2.uk.pool.ntp.org iburst
  - 3.uk.pool.ntp.org iburst
# Restrictions are used to control access to your ntpd
ntp_restricts:
  - "restrict 0.pool.ntp.org nomodify notrap noquery"
  - "restrict 1.pool.ntp.org nomodify notrap noquery"
  - "restrict 2.pool.ntp.org nomodify notrap noquery"
  - "restrict 3.pool.ntp.org nomodify notrap noquery"
  - "restrict default kod notrap nomodify nopeer noquery"
  - "restrict 127.0.0.1 nomodify"
  - "restrict -6 default kod notrap nomodify nopeer noquery"
  - "restrict -6 ::1 nomodify"
# File location wjere ntpd can find and store the clock drift
ntp_driftfile: "/var/lib/ntp/ntp.drift"
# Flag to control stat logging
ntp_log_stats: no
# Stat logging directory
ntp_statsdir: "/var/log/ntpstats/"
```

Useful links
------------

[ ntp.org: configuring NTP](http://support.ntp.org/bin/view/Support/ConfiguringNTP)

[ ntp.prg: documentation archive](http://doc.ntp.org/)

Example Playbook
----------------

    - hosts: servers
      roles:
         - ntp

License
-------

MIT
