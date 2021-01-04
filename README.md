# My Home Lab

![Ansible Lint](https://github.com/nleiva/ansible-home/workflows/Ansible%20Lint/badge.svg)

These are the playbooks I run in my personal lab.

## Dependencies

```bash
ansible-galaxy role install -r roles/requirements.yml
```

## Setup lab instances

```bash
ansible-playbook setup.yml --ask-become-pass -v
```