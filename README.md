# Ansible Role - Setup

Ansible role for deploying dotfiles and setup applications

# Requirements



# Examples


`roles/test/defauls/main.yml`
```
---
role_packages: []
role_copy: []
role_template: []
role_remove: []
role_download: []
role_execute: []
```

`roles/test/tasks/main.yml`
```
---
- name: Pass variables to the setup role
  import_role:
    name: setup
  tags:
    - test
```

`setup.yml`
```
---
- name: Setup Desktop Environment
  hosts: localhost

  roles:
    - role: test

```

# License
