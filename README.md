consul
=======

[![Ansible Role](https://img.shields.io/ansible/role/3300.svg)](https://galaxy.ansible.com/list#/roles/3300)

Installs and configures Consul

Requirements
------------

This role requires Ansible 1.4 or higher.

Role Variables
--------------

| Name                               | Default                                                          | Description                                                                                                                                                                                        |
|------------------------------------|------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| consul_version                     | 0.5.2                                                            | Version of Consul to install                                                                                                                                                                       |
| consul_sha256sum                   | 171cf4074bfca3b1e46112105738985783f19c47f4408377241b868affa9d445 | SHA 256 checksum of package                                                                                                                                                                        |
| consul_webui_version               | 0.5.2                                                            | Version of Consul webui to install                                                                                                                                                                 |
| consul_webui_sha256sum             | ad883aa52e1c0136ab1492bbcedad1210235f26d59719fb6de3ef6464f1ff3b1 | SHA 256 checksum of webui package                                                                                                                                                                  |
| consul_server                      | false                                                            | Enable server mode                                                                                                                                                                                 |
| consul_webui                       | false                                                            | Whether to install the Consul webui or not                                                                                                                                                         |
| consul_gomaxprocs                  | 1                                                                | Maxmimum GO processes                                                                                                                                                                              |
| consul_acl_datacenter              | ''                                                               | This designates the datacenter which is authoritative for ACL information                                                                                                                          |
| consul_acl_default_policy          | allow                                                            | Either "allow" or "deny". The default policy controls the behavior of a token when there is no matching rule                                                                                       |
| consul_acl_down_policy             | extend-cache                                                     | Either "allow", "deny" or "extend-cache". In the case that the policy for a token cannot be read from the acl_datacenter or leader node, the down policy is applied                                |
| consul_acl_master_token            | ''                                                               | This allows operators to bootstrap the ACL system with a token ID that is well-known                                                                                                               |
| consul_acl_token                   | ''                                                               | When provided, the agent will use this token when making requests to the Consul servers                                                                                                            |
| consul_acl_ttl                     | 30s                                                              | Used to control Time-To-Live caching of ACLs                                                                                                                                                       |
| consul_addresses_dns               | "{{ consul_client_addr }}"                                       | The DNS server address                                                                                                                                                                             |
| consul_addresses_http              | "{{ consul_client_addr }}"                                       | The HTTP API address                                                                                                                                                                               |
| consul_addresses_https             | "{{ consul_client_addr }}"                                       | The HTTPS API address                                                                                                                                                                              |
| consul_addresses_rpc               | "{{ consul_client_addr }}"                                       | The RPC endpoint address                                                                                                                                                                           |
| consul_advertise_addr              | ''                                                               | The advertise address is used to change the address that we advertise to other nodes in the cluster                                                                                                |
| consul_advertise_addr_wan          | ''                                                               | The advertise wan address is used to change the address that we advertise to server nodes joining through the WAN                                                                                  |
| consul_atlas_acl_token             | ''                                                               | When provided, any requests made by Atlas will use this ACL token unless explicitly overriden                                                                                                      |
| consul_atlas_infrastructure        | ''                                                               | This is used to provide the Atlas infrastructure name and the SCADA connection                                                                                                                     |
| consul_atlas_join                  | false                                                            | When set, enables auto-join via Atlas                                                                                                                                                              |
| consul_atlas_token                 | ''                                                               | Provides the Atlas API authentication token                                                                                                                                                        |
| consul_bind_addr                   | 0.0.0.0                                                          | The address that should be bound to for internal cluster communications                                                                                                                            |
| consul_bootstrap_expect            | 3                                                                | Number of expected servers in datacenter                                                                                                                                                           |
| consul_ca_file                     | ''                                                               | This provides a file path to a PEM-encoded certificate authority                                                                                                                                   |
| consul_cert_file                   | ''                                                               | This provides a file path to a PEM-encoded certificate                                                                                                                                             |
| consul_check_update_interval       | 5m                                                               | This interval controls how often check output from checks in a steady state is synchronized with the server                                                                                        |
| consul_client_addr                 | 127.0.0.1                                                        | The address to which Consul will bind client interfaces, including the HTTP, DNS, and RPC servers                                                                                                  |
| consul_datacenter                  | dc1                                                              | This flag controls the datacenter in which the agent is running                                                                                                                                    |
| consul_disable_anonymous_signature | false                                                            | Disables providing an anonymous signature for de-duplication with the update check                                                                                                                 |
| consul_disable_remote_exec         | false                                                            | Disables support for remote execution. When set to true, the agent will ignore any incoming remote exec requests                                                                                   |
| consul_disable_update_check        | false                                                            | Disables automatic checking for security bulletins and new version releases                                                                                                                        |
| consul_dns_config_allow_stale      | false                                                            | Enables a stale query for DNS information                                                                                                                                                          |
| consul_dns_config_max_stale        | 5s                                                               | When allow_stale is specified, this is used to limit how stale results are allowed to be                                                                                                           |
| consul_dns_node_ttl                | 0s                                                               | DNS caching for node lookups can be enabled by setting this value                                                                                                                                  |
| consul_dns_service_ttl             | ''                                                               | DNS caching for service lookups can be enabled by setting this value                                                                                                                               |
| consul_dns_enable_truncate         | false                                                            | If set to true, a UDP DNS query that would return more than 3 records will set the truncated flag, indicating to clients that they should re-query using TCP to get the full set of records        |
| consul_dns_only_passing            | false                                                            | If set to true, any nodes whose healthchecks are not passing will be excluded from DNS results                                                                                                     |
| consul_domain                      | ''                                                               | This flag can be used to change the domain                                                                                                                                                         |
| consul_enable_debug                | false                                                            | When set, enables some additional debugging features                                                                                                                                               |
| consul_enable_syslog               | false                                                            | This flag enables logging to syslog                                                                                                                                                                |
| consul_encrypt                     | ''                                                               | Specifies the secret key to use for encryption of Consul network traffic. This key must be 16-bytes that are Base64-encoded. The easiest way to create an encryption key is to use "consul keygen" |
| consul_http_api_response_headers   | {}                                                               | This object allows adding headers to the HTTP API responses                                                                                                                                        |
| consul_key_file                    | ''                                                               | This provides a the file path to a PEM-encoded private key                                                                                                                                         |
| consul_leave_on_terminate          | false                                                            | If enabled, when the agent receives a TERM signal, it will send a "Leave" message to the rest of the cluster and gracefully leave                                                                  |
| consul_log_level                   | info                                                             | The level of logging to show after the Consul agent has started. The available log levels are "trace", "debug", "info", "warn", and "err"                                                          |
| consul_node_name                   | ''                                                               | The name of this node in the cluster                                                                                                                                                               |
| consul_ports_dns                   | 8600                                                             | The DNS server port, -1 to disable                                                                                                                                                                 |
| consul_ports_http                  | 8500                                                             | The HTTP API port, -1 to disable                                                                                                                                                                   |
| consul_ports_https                 | -1                                                               | The HTTPS API port, -1 to disable                                                                                                                                                                  |
| consul_ports_rpc                   | 8400                                                             | The RPC endpoint port                                                                                                                                                                              |
| consul_ports_serf_lan              | 8301                                                             | The Serf LAN port                                                                                                                                                                                  |
| consul_ports_serf_wan              | 8302                                                             | The Serf WAN port                                                                                                                                                                                  |
| consul_ports_server                | 8300                                                             | The server RPC port                                                                                                                                                                                |
| consul_protocol                    | ''                                                               | The Consul protocol version to use. This defaults to the latest version. This should be set only when upgrading                                                                                    |
| consul_recursors                   | []                                                               | This flag provides addresses of upstream DNS servers that are used to recursively resolve queries if they are not inside the service domain for consul                                             |
| consul_rejoin_after_leave          | false                                                            | When provided, Consul will ignore a previous leave and attempt to rejoin the cluster when starting                                                                                                 |
| consul_retry_interval              | 30s                                                              | Time to wait between join attempts                                                                                                                                                                 |
| consul_retry_interval_wan          | 30s                                                              | Time to wait between join-wan attempts                                                                                                                                                             |
| consul_retry_join                  | []                                                               | Takes a list of addresses to attempt joining every retry_interval until at least one join works                                                                                                    |
| consul_retry_join_wan              | []                                                               | Takes a list of addresses to attempt joining to WAN every retry_interval_wan until at least one join-wan works                                                                                     |
| consul_server_name                 | ''                                                               | When provided, this overrides the node_name for the TLS certificate                                                                                                                                |
| consul_session_ttl_min             | 10s                                                              | The minimum allowed session TTL                                                                                                                                                                    |
| consul_skip_leave_on_interrupt     | false                                                            | This is similar to leave_on_terminate but only affects interrupt handling                                                                                                                          |
| consul_start_join                  | []                                                               | Addresses of agents to join upon starting up                                                                                                                                                       |
| consul_start_join_wan              | []                                                               | An array of strings specifying addresses of WAN nodes to join-wan upon startup                                                                                                                     |
| consul_statsd_addr                 | ''                                                               | This provides the address of a statsd instance                                                                                                                                                     |
| consul_statsite_addr               | ''                                                               | This provides the address of a statsite instance                                                                                                                                                   |
| consul_statsite_prefix             | consul                                                           | The prefix used while writing all telemetry data to statsite                                                                                                                                       |
| consul_syslog_facility             | LOCAL0                                                           | When enable_syslog is provided, this controls to which facility messages are sent                                                                                                                  |
| consul_ui_dir                      | "{{ consul_webui_install_dir }}/dist"                            | This flag provides the directory containing the Web UI resources for Consul                                                                                                                        |
| consul_verify_incoming             | false                                                            | If set to true, Consul requires that all incoming connections make use of TLS and that the client provides a certificate signed by the Certificate Authority from the ca_file                      |
| consul_verify_outgoing             | false                                                            | If set to true, Consul requires that all outgoing connections make use of TLS and that the server provides a certificate that is signed by the Certificate Authority from the ca_file              |
| consul_verify_server_hostname      | false                                                            | If set to true, Consul verifies for all outgoing connections that the TLS certificate presented by the servers matches "server.." hostname                                                         |
| consul_services                    | []                                                               | List of service definitions                                                                                                                                                                        |
| consul_checks                      | []                                                               | List of check definitions                                                                                                                                                                          |
| consul_watches                     | []                                                               | List of watch definitions                                                                                                                                                                          |

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

Install Consul with webui
```
- hosts: all
  roles:
    - { role: kbrebanov.consul, consul_webui: true }
```

Install Consul as a server
```
- hosts: all
  roles:
    - { role: kbrebanov.consul, consul_server: true }
```

Install Consul and configure a service
```
- hosts: all
  vars:
    consul_services:
      - name: "web"
        tags:
          - "rails"
        port: 80
  roles:
    - kbrebanov.consul
```

Install Consul and configure a check
```
- hosts: all
  vars:
    consul_checks:
      - name: "Web check"
        http: "http://localhost"
        interval: "10s"
        timeout: "1s"
  roles:
    - kbrebanov.consul
```

Install Consul and configure a watch
```
- hosts: all
  vars:
    consul_watches:
      - type: "service"
        service: "redis"
        handler: "/usr/bin/my-service-handler.sh"
  roles:
    - kbrebanov.consul
```

License
-------

BSD

Author Information
------------------

Kevin Brebanov
