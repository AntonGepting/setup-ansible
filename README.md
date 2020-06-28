# Setup Ansible Role (Working Title)

## Description

Main purpose of the Setup Ansible Role is deploying dotfiles and setup
applications.  The role can be included in other roles and executed from the
playbook. The functions are:

- __install__ packages

    ```
    role_packages:
        - "vim"
        - "vim.gtk3"
    ```

- __copy__ files

    ```
    role_copy:
        - { src: ".vimrc", dest: "~/.vim/.vimrc" }
    ```

- __process__ templates

    ```
    role_template:
        - { src: "conky.conf.j2", dest: "~/.config/conky/conky.conf" }
    ```

- __remove__ files

    ```
    role_remove:
        - { src: "~/.vim/.vimrc.old" }
    ```

- __download__ files

    ```
    role_download:
        - src: "https://sh.rustup.rs"
          dest: "rustup.sh"
          checksum: "sha512:\
               39ce80b06b2ba8dd\
               74043e04cc973533\
               356c2135be3ee7dd\
               95b47a6ffd380eec\
               555d9e9103d539b1\
               639b3412fa973617\
               b8af97f647ffb13e\
               1f8c536936aaaab3"
    ```

- __execute__ files

    ```
    role_exec:
        - src: "rustup.sh"
          cmd: "sh rustup.sh -y"
    ```

## Requirements




## Examples


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

## License

`setup` ansible role is licensed under the MIT license. Please read the
[license file](LICENSE.md) in the repository for more information.

## See also

- [Ansible](https://ansible.com/)
- [Ansible Docs](https://docs.ansible.com/ansible/latest/#)
- [Galaxy](https://galaxy.ansible.com/)
- [Galaxy Docs](https://galaxy.ansible.com/docs/)
