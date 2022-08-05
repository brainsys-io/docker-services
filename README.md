Docker services
===============

The present role :
  - installs Docker on host
  - installs various services through containers and docker-compose manifest

It has been tested on :
  - Debian 9
  - Debian 10
  - Debian 11

Available services
------------------

  - Traefik
  - Watchtower
  - Grafana

Role variables
---------------

| Variable                                     | Type    | Choices                                                                            | Default                 | Comment         |
|----------------------------------------------|---------|------------------------------------------------------------------------------------|-------------------------|-----------------|

Dependencies
------------

None.

Example Playbook
----------------

```
  - hosts: example
    ignore_errors: "{{ ansible_check_mode }}" # ignore errors only in check mode !

    roles:
      - { role: docker-services, tags: ['docker-services'] }
```

Example variables
-----------------

```
  ---
  docker_services:
    - traefik
    - watchtower
    - grafana

  traefik_domain: 'mydomain.com'
  traefik_letsencrypt_email: 'cert@mydomain.com'
```

TODO
----

1. Traefik
    1. add variables for basic auth in templates
    2. choose between global auth vs service auth
2. Grafana
    1. Handle providers
    2. Handle custom dashboards
    3. Permit anonymous login and user login
3. OpenVPN
    1. needs to be implemented
4. SSHPortal
    1. needs to be implemented
5. Loki
    1. needs to be implemented
6. Promtail
    1. needs to be implemented
7. Gitlab
    1. needs to be implemented

License
-------

MIT Modern

Author Information
------------------

Written by Ludovic Cartier <ludovic.cartier@brainsys.io>
