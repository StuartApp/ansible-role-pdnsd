PDNSD
=========

An Ansible role that installs pdnsd on Debian linux.

Requirements
------------

None

Role Variables
--------------

Check `defaults/main.yml` for a list of default variables (the ones installed from debian).
The most important one will be pdnsd_config, where you can set the configuration of the service.

Dependencies
------------

None

Example Playbook
----------------
### Sample config for resolvconf upstream

Create config for servers in `group_vars`:
```
pdnsd_config: |-
  global {
      perm_cache=2048;
      cache_dir="/var/cache/pdnsd";
      run_as="nobody";
      server_ip = 0.0.0.0;
      status_ctl = on;
      min_ttl=15m;
      max_ttl=1w;
      timeout=10;
      neg_domain_pol=on;
      udpbufsize=1024;
  }
  server {
      label= "resolvconf";
      proxy_only=on;
      timeout=4;
  }
```

Install the service with the default configuration:

    - hosts: servers
      roles:
         - { role: stuart.pdnsd }


License
-------

Apache2

Author Information
------------------

Maintainer: m.puerta@stuart.com
Company: Stuart (https://wwww.stuart.com)
