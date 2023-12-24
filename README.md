# Ansible role [postgres](https://galaxy.ansible.com/ui/standalone/roles/buluma/postgres/documentation)

Install and configure postgres on your system.

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-postgres/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-postgres/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-postgres.svg)](https://github.com/buluma/ansible-role-postgres/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-postgres.svg)](https://github.com/buluma/ansible-role-postgres/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-postgres.svg)](https://github.com/buluma/ansible-role-postgres/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/postgres)](https://galaxy.ansible.com/ui/standalone/roles/buluma/postgres/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-postgres/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: buluma.postgres
      postgres_port: 6543
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-postgres/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap
    - role: buluma.buildtools
    - role: buluma.epel
    - role: buluma.python_pip
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-postgres/blob/master/defaults/main.yml):

```yaml
---
# defaults file for postgres

postgres_port: 5432
postgres_listen_addresses: "127.0.0.1"
postgres_unix_socket_directories: "{{ postgres_socket_directory }}"
postgres_max_wal_size: 1GB
postgres_min_wal_size: 80MB
postgres_log_timezone: UTC
postgres_datestyle: iso, ymd
postgres_timezone: UTC
postgres_default_text_search_config: pg_catalog.english

postgres_hba_entries:
  - type: local
    database: all
    user: all
    method: peer
  - type: host
    database: all
    user: all
    address: "127.0.0.1/32"
    method: ident
  - type: host
    database: all
    user: all
    address: "::1/128"
    method: ident
  - type: local
    database: replication
    user: all
    method: peer
  - type: host
    database: replication
    user: all
    address: "127.0.0.1/32"
    method: ident
  - type: host
    database: replication
    user: all
    address: "::1/128"
    method: ident
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-postgres/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.buildtools](https://galaxy.ansible.com/buluma/buildtools)|[![Ansible Molecule](https://github.com/buluma/ansible-role-buildtools/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-buildtools/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-buildtools.svg)](https://github.com/shadowwalker/ansible-role-buildtools)|
|[buluma.epel](https://galaxy.ansible.com/buluma/epel)|[![Ansible Molecule](https://github.com/buluma/ansible-role-epel/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-epel/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-epel.svg)](https://github.com/shadowwalker/ansible-role-epel)|
|[buluma.python_pip](https://galaxy.ansible.com/buluma/python_pip)|[![Ansible Molecule](https://github.com/buluma/ansible-role-python_pip/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-python_pip/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-python_pip.svg)](https://github.com/shadowwalker/ansible-role-python_pip)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-postgres/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Alpine](https://hub.docker.com/repository/docker/buluma/alpine/general)|all|
|[EL](https://hub.docker.com/repository/docker/buluma/enterpriselinux/general)|8|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|all|
|[Fedora](https://hub.docker.com/repository/docker/buluma/fedora/general)|all|
|[opensuse](https://hub.docker.com/repository/docker/buluma/opensuse/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|
|[Kali](https://hub.docker.com/repository/docker/buluma/kali/general)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-postgres/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-postgres/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-postgres/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)


Template inspired by [Robert de Bock](https://github.com/robertdebock)
