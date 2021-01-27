sleif.mariadb_docker
============

This role runs a mariadb instance on docker.

Requirements
------------

Use it on a machine setup with ansible role sleif.docker.

Role Variables
--------------
- container_storage_dir_base: '/srv' (don't place it on NFS volume)
- container_storage_dir_base_backup: '/srv'
- mariadb_container_max_connections: '512'
- mariadb_container_exposed_port: '3306'
- DOCKER_NETWORK_NAME (can be defined in sleif.docker)

Dependencies
------------

Needs geerlingguy.docker to make sure Docker is available.
Needs sleif.docker to make sure Docker is configured as needed.

Example Playbook
----------------

    - hosts: "server"
      user: root
      vars:
        DOCKER_NETWORK_NAME: 'custom_docker_network'
      roles:
        - { role: sleif.mariadb_docker, tags: "mariadb_docker" }

License
-------

MIT

Author Information
------------------

Created in 2021 by Sebastian Berthold
