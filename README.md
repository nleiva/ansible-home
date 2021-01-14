# My Home Lab

![Ansible Lint](https://github.com/nleiva/ansible-home/workflows/Ansible%20Lint/badge.svg)

These are the playbooks I run in my personal lab.

<p align="center">
  <img width="454" height="605" title="My Home Lab" src="static/home-lab.jpeg"><br>
  <b>Early setup of my lab</b><br>
</p>

## Requirements

` ssh-copy-id` to every host before running these playbooks. 

## Playbooks

### 1. Setup Lab instances

To perform some basic management tasks such as upgrading packages or updating Firewall rules:

```bash
ansible-playbook setup.yml --ask-become-pass -v
```

#### Dependencies

```bash
ansible-galaxy role install -r roles/requirements.yml
```

### 2. Install Pi-hole

To install Pi-hole:

```bash
ansible-playbook pi-hole.yml --ask-become-pass -v
```

To update the list of whitelisted websites per [WHITELIST](https://github.com/anudeepND/whitelist):

```bash
ansible-playbook pi-hole.yml --ask-become-pass -v --tags whitelist
```

[Block lists](https://firebog.net/) can be added via the [GUI](https://docs.pi-hole.net/database/gravity/example/).