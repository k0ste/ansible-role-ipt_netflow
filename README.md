ansible-role-ipt_netflow
============================

Role for deploy [ipt_netflow](//github.com/aabc/ipt-netflow) Linux module.

Ansible versions
--------------------
Role is adapted for Ansible 2.0, should work on 1.9.

Requirements for usage
-----------------------------------

* GNU/Linux distro with systemd for modules-load.d property work;
* ipt_NETFLOW module;

Extra
----------

The role support array of module options. Options is not validate and pass
as-is. All possible options, which receives by module depend of build. Read
[README of ipt_NETFLOW](//github.com/aabc/ipt-netflow/blob/master/README).

Role provide order of load modules, because all conntrack modules should load
before ipt_NETFLOW. Modules load to kernel at boot via
[modules.load.d](//www.freedesktop.org/software/systemd/man/modules-load.d.html)

Example configuration
-------------------------

```yaml
---
ipt_netflow:
  protocol: '5'
  destination: '127.0.0.1:2055'
  debug: '0'
  hashsize: '131072'
  maxflows: '0'
```
