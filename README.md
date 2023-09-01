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

```sh
ansible-galaxy install sleif.podman --force
ansible-galaxy install sleif.mariadb_container --force
```

## Example Playbook

```yml
- name: VM db.example.com
  hosts: "db.example.com"
  user: root
  vars:
    podman_networks:
      podman_network_root:
        podman_network_name: 'podman_custom'
        podman_network_subnet: '10.0.0.0/24'
        podman_network_gateway: '10.0.0.1'
        podman_network_iprange: '10.0.0.128/25'
      podman_network_rootless:
        podman_network_name: 'podman_custom'
        podman_network_subnet: '10.0.1.0/24'
        podman_network_gateway: '10.0.1.1'
        podman_network_iprange: '10.0.1.128/25'
    podman_rootless: true
    podman_network_name: "{{ podman_networks.podman_network_rootless.podman_network_name }}"

  roles:
    - {role: sleif.podman, tags: "podman_role",
       podman_operation: "podman_install"}
    - {role: sleif.mariadb_container, tags: "mariadb_container",
       pod_name: "app_with-db"}
```

## License

MIT

## Author Information

Created in 2023 by Sebastian Berthold
