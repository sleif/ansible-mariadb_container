# sleif.mariadb_container

This role runs a MariaDB instance on Podman.

## Requirements

- Podman installed

## Role Variables

- container_storage_dir_base_local: '/srv' (don't place it on NFS volume)
- container_storage_dir_base: '/srv'
- mariadb_container_max_connections: '512'
- mariadb_container_exposed_port: '3306'
- mariadb_container_image_tag: '10.6'

## Dependencies

N/A

## Example Playbook

    - hosts: "server"
      user: root
      roles:
        - { role: sleif.mariadb_container, tags: "mariadb_container" }

## License

MIT

## Author Information

Created in 2021 by Sebastian Berthold
