Description
===========

This directory contains a sample module, which extends functionality of Zabbix Agent. 

Status
======

This module is testing and for zabbix version 2.x.

Installation
============

```bash

	$ git clone https://github.com/cnshawncao/zabbix-module-memcached.git
	$ cp -r zabbix-module-memcached zabbix-x.x.x/src/modules/memcached	# zabbix-x.x.x is zabbix version
	$ cd zabbix-x.x.x/src/modules/memcached	# zabbix-x.x.x is zabbix version
```

1. run 'make' to build it. It should produce memcached.so.

1. copy memcached.so to the module directory, like LoadModulePath=/etc/zabbix/modules

1. change config file add line : LoadModule=memcached.so

1. cp zbx_module_memcached.conf to /etc/zabbix, modify it


    memcached_inst_ports = 11211, 192.168.9.9:11212, 11213

1. restart zabbix_agent daemon

1. import the zabbix template *zbx_template_memcached_active.xml*

1. link template *zbx_template_memcached_active.xml*

Synopsis
========

**key:** *memcached.discovery*

**value:**

    {"data":[{"{#MCHOST}":"127.0.0.1","{#MCPORT}":"11211"},{"{#MCHOST}":"192.168.9.9","{#MCPORT}":"11212"},{"{#MCHOST}":"127.0.0.1","{#MCPORT}":"11213"}]}
    
**key:** *memcached.status[{#MCHOST},{#MCPORT},key]*

**key:** *memcached.ping[{#MCHOST},{#MCPORT}]*

Note
===

Note: this module only support the digit value, other key will return: ZBX_NOTSUPPORTED: Not supported key
