# sleif.mariadb_container

This role runs a MariaDB instance on Podman.

## Requirements

Use it on a machine setup with ansible role sleif.podman.

## Role Variables

- container_storage_dir_base: '/srv' (don't place it on NFS volume)
- container_storage_dir_base_backup: '/srv'
- mariadb_container_max_connections: '512'
- mariadb_container_exposed_port: '3306'

## Dependencies

N/A

## Example Playbook

    - hosts: "server"
      user: root
      <!-- vars:
        DOCKER_NETWORK_NAME: 'custom_docker_network' -->
      roles:
        - { role: sleif.mariadb_container, tags: "mariadb_container" }

## License

MIT

## Author Information

Created in 2021 by Sebastian Berthold
