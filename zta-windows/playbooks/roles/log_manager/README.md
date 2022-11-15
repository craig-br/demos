log_manager
===========

An [Ansible](https://ansible.com) role to manage logs in many firewall devices.

Current supported list of providers:
* checkpoint
* trendmicro

Requirements
------------
Red Hat Enterprise Linux 7.x, or derived Linux distribution such as CentOS 7,
Scientific Linux 7, etc

For TrendMicro provider to work with log_manager as expected
user should have [TrendMicro DeepSecurity collection](https://galaxy.ansible.com/trendmicro/deepsec) installed

Functions
---------

* `forward_logs_to_syslog` - This forwards logs of the firewall device to an external syslog server
* `unforward_logs_to_syslog` - This unforwards logs of the firewall device to an external syslog server

Example Playbook
----------------

* Checkpoint

```
- hosts: checkpoint
  connection: httpapi

  tasks: 
    - include_role:
        name: log_manager
        tasks_from: forward_logs_to_syslog
      vars:
        syslog_server: 192.168.0.1
        checkpoint_server_name: test
        firewall_provider: checkpoint

```

* TrendMicro Deepsecurity

1. Create a Syslog config and as mentioned in TM Deepsec collection [Readme](https://github.com/ansible-collections/trendmicro.deepsec#using-trendmicro-deepsecurity-ansible-collection)
   As Syslog has legacy TM REST API implementation it uses inventory which
   requires `ansible_user` and `ansible_httpapi_pass` in inventory file.

```
- hosts: deepsec
  connection: httpapi

  tasks:
    - include_role:
        name: log_manager
        tasks_from: create_syslog_config
      vars:
        syslog_server: 192.168.0.1
        trendmicro_syslog_config_name: test
        firewall_provider: trendmicro
        state: present
```

2. Now, that we have created Syslog Config policy, we need to register the policy
   under System Settings Event Forwarding parameter. Keep in mind the System settings
   belongs to the newer REST API where the user is expected to pass `api_key` under their
   inventory file for the role to update the required settings

```
- hosts: deepsec
  connection: httpapi

  tasks:
    - include_role:
        name: log_manager
        tasks_from: forward_logs_to_syslog
      vars:
        firewall_provider: trendmicro
        state: present
```


License
-------

GPLv3

Author Information
------------------

[Ansible Security Automation Team](https://github.com/ansible-security)
