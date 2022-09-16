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
  - Maildev

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
    - maildev

  traefik_domain: 'mydomain.com'
  traefik_letsencrypt_email: 'cert@mydomain.com'

  maildev_domain: 'maildev.mydomain.com'
```

TODO
----

- Traefik
  - add variables for basic auth in templates
  - choose between global auth vs service auth
- Grafana
  - Handle providers
  - Handle custom dashboards
  - Permit anonymous login and user login
- OpenVPN
  - needs to be implemented
- SSHPortal
  - needs to be implemented
- Loki
  - needs to be implemented
- Promtail
  - needs to be implemented
- Gitlab
  - needs to be implemented

License
-------

MIT Modern

Author Information
------------------

Written by Ludovic Cartier <ludovic.cartier@brainsys.io>
