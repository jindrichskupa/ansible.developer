Developer Access Ansible Role
=========

Manage developer accounts, ssh keys and passwordless sudo.

Requirements
------------

* debian based distribution

Example Playbook
----------------

```yaml
---
- name: Manage server access
  hosts: all
  remote_user: debian
  become: true
  vars:
    ansible_python_interpreter: /usr/bin/python3
    docker_compose_dirs: []
  vars_files:
    - /etc/ansible/vars/all.yml
  roles:
    - role: developer
      vars:
        github_base_url: https://gitlab.com
        developers:
          # grant user access
          - name: "Karel Novak"
            login: "karel.novak"
            github: "karel.novak"
            groups: docker
            state: "present"
          # remove user acccess 
          - name: "Josef Novak"
            login: "josef.novak"
            github: "josef.novak"
            groups: docker
            state: "absent"
```

License
-------

MIT

Author Information
------------------

Jindrich Skupa
