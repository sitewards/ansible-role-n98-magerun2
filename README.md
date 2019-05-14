# Ansible n98 Magerun 2 Role

This is the Ansible role to install n98-magerun for Magento 2. It's designed for 
consumption by playbooks, not for consumption by itself.
It installs a version of n98 magerun2 into the project.

## Limitations

- It is not hugely portable. It was open sourced as part of an effort to make it so
- It requires infrastructure tailored in a particular format, which is currently undocumented.

## Installation

There are two ways to install this role:

### Ansible Galaxy (recommended)

```bash
$ cd path/to/playbook/root
$ cat >> requirements.yaml <<EOF
- src: "https://github.com/sitewards/ansible-role-n98-magerun2"
  version: "d5b1404" # <----- Update this to a stable version
  name: "sitewards.n98-magerun2"
EOF
$ ansible-galaxy install -r requirements.yaml
```

### Git Submodules

```bash
$ cd path/to/playbook/root
$ mkdir roles/
$ git submodule add https://github.com/littlemanco/ansible-role-n98-magerun2 roles/sitewards.n98-magerun2
```

## Usage

Include this in another ansible playbook. For sample, consider a generic server playbook:

```yaml
---
# $PLAYBOOK_ROOT/server.yaml
- name: "server"
  hosts: all
  become: true
  become_user: "root"
```

Add the reference for the role:

```yaml
# $PLAYBOOK_ROOT/server.yaml
# ...
become_user: "root"
roles
  - "sitewards.n98-magerun2"
```

This will allow the role to be discovered. That's it!

## Configuration

Configuration is defined in `defaults/main.yml`. It must be configured before use.

## Contact

- Web: https://www.sitewards.com/
