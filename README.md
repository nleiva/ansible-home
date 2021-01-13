# My Home Lab

![Ansible Lint](https://github.com/nleiva/ansible-home/workflows/Ansible%20Lint/badge.svg)

These are the playbooks I run in my personal lab.

## Requirements

` ssh-copy-id` every host before running these playbooks. 

## Playbooks

### Setup Lab instances

```bash
ansible-playbook setup.yml --ask-become-pass -v
```

#### Dependencies

```bash
ansible-galaxy role install -r roles/requirements.yml
```

### Install Pi-hole

```bash
ansible-playbook pi-hole.yml --ask-become-pass -v
```