# My Home Lab

![Ansible Lint](https://github.com/nleiva/ansible-home/workflows/Ansible%20Lint/badge.svg)

These are the playbooks I run in my personal lab.

## Update software packages

```bash
ansible-playbook update_pkg.yml --ask-become-pass -v
```