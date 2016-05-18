ansible-ocs
=========

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-franlr--ocs-blue.svg)](https://galaxy.ansible.com/list#/roles/4468)

An Ansible role for installing ocsinventory-agent.

This role only works with the ocsinventory-agent 2.1 or later to let the agent be installed non-interactively (http://wiki.ocsinventory-ng.org/index.php/Documentation:UnixAgent).

Tested on:
- Ubuntu 14.04 and 16.04
- CentOS 6 and 7
- Debian 7 and 8

Requirements
------------

None.
 
Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Available variables are listed below, along with default values (see `defaults/main.yml`):

```
---
ocs_name: "Ocsinventory-Unix-Agent"
ocs_agent_version: "2.1.1"
ocs_archive: "{{ ocs_name }}-{{ ocs_agent_version }}"
ocs_pkg: "{{ ocs_archive }}.tar.gz"
ocs_down_url: "https://github.com/OCSInventory-NG/UnixAgent/releases/download/{{ ocs_agent_version }}/{{ ocs_pkg }}"
ocs_down_dir: /tmp
ocs_server: ocsinventory-server.domain.name
ocs_basedir: /var/lib/ocsinventory-agent
ocs_configdir: /etc/ocsinventory
ocs_tag: srvtype
ocs_logfile: /var/log/ocsinventory-agent.log
ocs_options: --crontab --remove-old-linux-agent --debug --download --snmp --now
ocs_ssl: false
ocs_ca:
```

Dependencies
------------

Development tools and perl dependencies are included into roles's requirements. This role installs and uses CPAN to install perl 'Digest::MD5'.

Example Playbook
----------------

How to use this role:

``` yml
---
- hosts: all
  gather_facts: true
  sudo: yes
  roles:
    - ocs_agent
  vars:
    - ocs_server: ocs.mydomain.com
    - ocs_ssl: true
    - ocs_tag: "{{ ansible_hostname }}"
```

License
-------

Apache v2.0

Author Information
------------------

This role was created in 2015 by [FranLR](https://github.com/franlr/)

Updated by paulbsd
