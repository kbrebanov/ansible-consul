consul
=======

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-kbrebanov.consul-660198.svg)](https://galaxy.ansible.com/list#/roles/3300)

Installs Consul

Requirements
------------

This role requires Ansible 1.4 or higher.

Role Variables
--------------

| Name             | Default                                                          | Description                  |
|------------------|------------------------------------------------------------------|------------------------------|
| consul_version   | 0.5.1                                                            | Version of Consul to install |
| consul_sha256sum | 967ad75865b950698833eaf26415ba48d8a22befb5d4e8c77630ad70f251b100 | SHA 256 checksum of package  |

Dependencies
------------

- kbrebanov.unzip

Example Playbook
----------------

Install Consul
```
- hosts: all
  roles:
    - { role: kbrebanov.consul }
```

Install Consul specifying version and checksum
```
- hosts: all
  roles:
    - { role: kbrebanov.consul, consul_version: 0.4.1, consul_sha256sum: 2cf6e59edf348c3094c721eb77436e8c789afa2c35e6e3123a804edfeb1744ac }
```

License
-------

BSD

Author Information
------------------

Kevin Brebanov
