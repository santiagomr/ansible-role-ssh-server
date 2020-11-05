Ansible role ssh_server
=========
[![Build Status](https://travis-ci.com/santiagomr/ansible-role-ssh-server.svg?branch=master)](https://travis-ci.com/github/santiagomr/ansible-role-ssh-server)
[![Galaxy](https://img.shields.io/badge/galaxy-santiagomr.ssh_server-blue.svg)](https://galaxy.ansible.com/santiagomr/ssh_server)

Ansible role to automate SSH Server configuration on Debian-based systems, focused on security aspects.

Requirements
------------

Ansible >= 2.7

Role Variables
--------------

```yaml
# Allows you to customize the server motd if one is indicated
ssh_custom_motd_path: "{{ playbook_dir }}/files/etc/motd/{{ inventory_hostname.split('.')[0] }}"
ssh_server_listen_port: 22
ssh_server_listen_protocol: 2

ssh_server_login_grace_time: 2m
ssh_server_permit_root_login: "prohibit-password" # prohibit-password - yes - no
ssh_server_strict_modes: "yes"
ssh_server_max_auth_tries: 6
ssh_server_max_sessions: 10
ssh_server_pubkey_authentication: "yes"
ssh_server_password_authentication: "no" # yes or no
ssh_server_permit_empty_passwords: "no"

ssh_server_use_PAM: "yes"

ssh_server_allow_users:
  - myself

ssh_server_allow_tcp_forwarding: "yes"

ssh_server_x11forwarding: "yes"

ssh_server_permit_TTY: "yes"
ssh_server_print_motd: "no"
ssh_server_print_last_log: "yes"
ssh_server_TCP_keep_alive: "yes"
ssh_server_client_alive_interval: 0
ssh_server_client_alive_count_max: 3
ssh_server_max_startups: "10:30:100"

ssh_server_sftp_enabled: false
```

Dependencies
------------

No dependencies

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - role: santiagomr.ssh-server
      ssh_custom_motd_path: "etc/motd/{{ inventory_hostname.split('.')[0] }}"
      ssh_server_listen_port: 2222
      ssh_server_permit_root_login: "no"
      ssh_server_pubkey_authentication: "yes"
      ssh_server_password_authentication: "no"
      ssh_server_permit_empty_passwords: "no"
      ssh_server_use_PAM: "yes"
      ssh_server_allow_users:
        - myself
```


License
-------

GPL-v3

Author Information
------------------

[@santiagomr](https://github.com/santiagomr)
