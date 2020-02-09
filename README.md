Role Name
=========

locatedb: Locatedb

[![Build Status](https://travis-ci.org/cmihai-ansible/locatedb.svg?branch=master)](https://travis-ci.org/cmihai-ansible/locatedb)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.locatedb](https://galaxy.ansible.com/devopstoolbox.locatedb)

```bash
ansible-galaxy install devopstoolbox.locatedb
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
locatedb_packages_state: present
locatedb_remove_packages: true
locatedb_enable_service: true
locatedb_enable_selinux: true
locatedb_copy_templates: true
locatedb_firewall_configure: true
locatedb_firewall_rules:
  - service: ssh
  - port: 3389
locatedb_users:
  - user: devops
    group: docker
locatedb_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install locatedb on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: locatedb is configured
      import_role:
        name: devopstoolbox.locatedb
      vars:
        locatedb_packages_state: present
        locatedb_remove_packages: true
        locatedb_enable_service: true
        locatedb_enable_selinux: true
        locatedb_copy_templates: true
        locatedb_firewall_configure: true
        locatedb_firewall_rules:
          - service: ssh
          - port: 3389
        locatedb_users:
          - user: devops
            group: docker
        locatedb_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: locatedb
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
