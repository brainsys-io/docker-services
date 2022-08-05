Docker services
===============

The present role :
  - installs Docker on host
  - installs various services through containers and docker-compose manifest

It has bienn tested on :
  - Debian 9
  - Debian 10
  - Debian 11

Role variables
---------------

| Variable                                     | Type    | Choices                                                                            | Default                 | Comment         |
|----------------------------------------------|---------|------------------------------------------------------------------------------------|-------------------------|-----------------|

Dependencies
------------

None.

Example Playbook
----------------

  - hosts: example
    ignore_errors: "{{ ansible_check_mode }}" # ignore errors only in check mode !

    roles:
      - { role: docker-services, tags: ['docker-services'] }

Example variables
-----------------

  ---
  docker_services:
    - traefik
    - watchtower
    - grafana

  traefik_domain: 'mydomain.com'
  traefik_letsencrypt_email: 'cert@mydomain.com'

TODO
----

License
-------

MIT Modern

Author Information
------------------

Written by Ludovic Cartier <ludovic.cartier@brainsys.io>
