# My Home Lab

![Ansible Lint](https://github.com/nleiva/ansible-home/workflows/Ansible%20Lint/badge.svg)

These are the playbooks I run in my personal lab.

## Requirements

` ssh-copy-id` every host before running these playbooks. 

## Setup Lab instances

```bash
ansible-playbook setup.yml --ask-become-pass -v
```

### Dependencies

```bash
ansible-galaxy role install -r roles/requirements.yml
```


## Run a Pi-hole Container

```bash
ansible-playbook pi-hole.yml --ask-become-pass -v
```

### Dependencies

```bash
ansible-galaxy collection install containers.podman
```

### Systemd Unit

Create `/etc/systemd/system/pihole.service`:

```ini
[Unit]
Description=Podman Container Service
Wants=network.target
After=network-online.target

[Service]
Restart=on-failure
ExecStart=/usr/bin/podman start -a pihole
ExecStop=/usr/bin/podman stop -t 10 pihole

[Install]
WantedBy=multi-user.target default.target
```

Then run:

```bash
setsebool -P container_manage_cgroup on
systemctl daemon-reload
systemctl enable pihole.service
```