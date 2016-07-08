provision_docker
================

[![Ansible Galaxy][galaxy_image]][galaxy_link]
[![Build Status][travis_image]][travis_link]
[![Latest Tag][tag_image]][tag_link]

An [Ansible](https://www.ansible.com/) role to provision [Docker](https://www.docker.com/) containers, mostly for Ansible role testing purposes.

Docker images designed for Ansible role testing purposes, running systemd init system and openssh server.
```
tomashavlas/ansible-test:centos7
tomashavlas/ansible-test:debian8
```
Dockerfiles for listed images are stored in GitHub repository [tomashavlas/docker-images](https://github.com/tomashavlas/docker-images) in [ansible-test](https://github.com/tomashavlas/docker-images/tree/ansible-test) branch.

Requirements
------------

This role requires following packages to be installed:

- `docker-py` to manage docker packages with ansible,
- `sshpass` to allow non-interactive password authentication to ssh server.

Role Variables
--------------

```yaml
# state of provisioned Docker containers
provision_docker__container_state: 'started'

# list of provisioned Docker containers with parameters
provision_docker__inventory: []
## name of container
#  - name: string
## base image of container
#    image: string
## OPTIONAL: should be container run with extended privileges
#    privileged: bool
## OPTIONAL: container hostname
#    hostname: string
## OPTIONAL: list of container shared volumes
#    volumes: [ string ]

# default Ansible inventory groups for provisioned Docker containers,
# appends to existing groups specified in inventory file
provision_docker__inventory_groups:
  - 'provision_docker__containers'

# default user for SSH connection to Docker containers,
# can be overriden pre host in inventory file through variable ansible_ssh_user
provision_docker__ssh_user: 'root'

# default password for SSH connection to Docker containers,
# can be overriden per host in inventory file through variable ansible_ssh_pass
provision_docker__ssh_pass: 'docker.io'
```

Dependencies
------------

None.

Example Playbook
----------------

Sample playbook to initialize two Docker containers.
```yaml
- hosts: localhost
  roles:
    - role: 'tomashavlas.provision_docker'
      provision_docker__inventory:
        - name: 'sample_centos7'
          image: 'tomashavlas/ansible-test:centos7'
          volumes:
            - '/sys/fs/cgroup:/sys/fs/cgroup:ro'
        - name: 'sample_debian8'
          image: 'tomashavlas/ansible-test:debian8'
          volumes:
            - '/sys/fs/cgroup:/sys/fs/cgroup:ro'
```

More advanced examples can be found in test scenarios of [these Ansible roles](https://github.com/search?q=user%3Atomashavlas+ansible-role).

License
-------

BSD

Author Information
------------------

Created by [Tomáš Havlas](https://github.com/tomashavlas) in 2016.

Based on [Chris Meyers's](https://github.com/chrismeyersfsu) idea and Ansible role [provision_docker](https://github.com/chrismeyersfsu/provision_docker).


[galaxy_image]: https://img.shields.io/badge/galaxy-tomashavlas.provision__docker-blue.svg?style=flat
[galaxy_link]: https://galaxy.ansible.com/tomashavlas/provision_docker/
[tag_image]: https://img.shields.io/github/tag/tomashavlas/ansible-role-provision_docker.svg
[tag_link]: https://github.com/tomashavlas/ansible-role-provision_docker/tags
[travis_image]: https://travis-ci.org/tomashavlas/ansible-role-provision_docker.svg?branch=master
[travis_link]: https://travis-ci.org/tomashavlas/ansible-role-provision_docker/
