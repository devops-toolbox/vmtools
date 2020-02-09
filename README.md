Role Name
=========

vmtools: Vmtools

[![Build Status](https://travis-ci.org/cmihai-ansible/vmtools.svg?branch=master)](https://travis-ci.org/cmihai-ansible/vmtools)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.vmtools](https://galaxy.ansible.com/devopstoolbox.vmtools)

```bash
ansible-galaxy install devopstoolbox.vmtools
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
vmtools_packages_state: present
vmtools_remove_packages: true
vmtools_enable_service: true
vmtools_enable_selinux: true
vmtools_copy_templates: true
vmtools_firewall_configure: true
vmtools_firewall_rules:
  - service: ssh
  - port: 3389
vmtools_users:
  - user: devops
    group: docker
vmtools_selinux_booleans:
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
- name: Install vmtools on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: vmtools is configured
      import_role:
        name: devopstoolbox.vmtools
      vars:
        vmtools_packages_state: present
        vmtools_remove_packages: true
        vmtools_enable_service: true
        vmtools_enable_selinux: true
        vmtools_copy_templates: true
        vmtools_firewall_configure: true
        vmtools_firewall_rules:
          - service: ssh
          - port: 3389
        vmtools_users:
          - user: devops
            group: docker
        vmtools_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: vmtools
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
