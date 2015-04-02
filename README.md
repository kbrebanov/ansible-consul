consul
=======

Installs Consul

Requirements
------------

This role requires Ansible 1.4 or higher.

Role Variables
--------------

| Name             | Default                                                          | Description                  |
|------------------|------------------------------------------------------------------|------------------------------|
| consul_version   | 0.5.0                                                            | Version of Consul to install |
| consul_sha256sum | 161f2a8803e31550bd92a00e95a3a517aa949714c19d3124c46e56cfdc97b088 | SHA 256 checksum of package  |

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
