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
  - cadvisor
  - Redisinsight

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
    - cadvisor
    - redisinsight

  traefik_domain: 'mydomain.com'
  traefik_letsencrypt_email: 'cert@mydomain.com'
  traefik_ipwhitelist: '42.42.42.42/32, 192.168.1.0/24, 127.0.0.1/32'

  maildev_domain: 'maildev.mydomain.com'

  redisinsight_domain: 'redisinsight.mydomain.com'
  redisinsight_whitelist:
	- 192.168.1.0/24
	- 31.15.24.XX
	- 37.58.179.XX
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
