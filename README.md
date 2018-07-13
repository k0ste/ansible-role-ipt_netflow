# ansible-role-ipt_netflow

Role for deploy [ipt_netflow](//github.com/aabc/ipt-netflow) Linux module.

The role support array of module options. All possible options, which receives
by module depend of build. Option keys are validate by the template, for all
possible options consult with
[README of ipt_NETFLOW](//github.com/aabc/ipt-netflow/blob/master/README).

Role provide order of load modules, because all conntrack modules should load
before ipt_NETFLOW. Modules load to kernel at boot via
[modules.load.d](//freedesktop.org/software/systemd/man/modules-load.d.html).

## Requirements

* Ansible 2.5+;
* GNU/Linux distro with `systemd` for modules-load.d property work;
* `ipt_NETFLOW` module;

## Example configuration

```yaml
---
# Install ipt_netflow package or not.
ipt_netflow_install_package: 'true'
# Reload or not systemd-modules-load service. This will insert not loaded
# modules to the kernel. This is not affected on already loaded modules.
ipt_netflow_modules_reload: 'true'

ipt_netflow:
  protocol: '5'
  destination: '127.0.0.1:2055'
  debug: '0'
  hashsize: '131072'
  maxflows: '0'
```
