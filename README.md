nxos_upgrade
=========
[![Build Status](https://travis-ci.org/bobbywatson3/nxos_upgrade.svg?branch=master)](https://travis-ci.org/robertwatson3/nxos_upgrade)

Installs NXOS and EPLD firmware on Nexus OS devices.

Requirements
------------

- Ansible 2.0
- pexpect (pip install pexpect)
- nxos-ansible modules (https://github.com/jedelman8/nxos-ansible.git)
- feature nxapi
- Firmware must already be on bootflash of switch

Role Variables
--------------
```YAML
firmware_nxos_filename: NXOS filename
firmware_epld_filename: EPLD filename
switch_username: user
switch_password: password
```

Example Playbook
----------------
```YAML
---
- hosts: nxos
  connection: local
  gather_facts: yes
  force_handlers: True
  
  vars_prompt:
   - name: switch_username
     prompt: "What is the switch username?"
     private: False
   - name: switch_password
     prompt: "What is the switch password?"
  
  vars:
    firmware_nxos_filename: n9000-dk9.1.0.0.bin
    firmware_epld_filename: n9000-epld.1.0.0.img
  
  roles:
    - nxos_upgrade
```
License
-------

BSD

Author Information
------------------

Bobby Watson (bwatsoni@cisco.com, robertwatson3@gmail.com)
