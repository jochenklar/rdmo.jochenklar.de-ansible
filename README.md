rdmo-ansible
============

A *simple* ansible playbook to deploy [RDMO](https://rdmorganiser.github.io) (with PostgresSQL and Gunicorn).

Setup
-----

Create a `hosts` file with the hostname of your RDMO machine and the following variables:

```plain
[rdmo]
rdmo.jochenklar.de

[rdmo:vars]
repository=https://github.com/jochenklar/rdmo.jochenklar.de
requirements=rdmo[allauth,gunicorn,postgres]
local_py=local.py                    # the config/settings/local.py
fixtures=fixtures.json               # a optional file with fixtures
rdmo_service=rdmo.service            # the systemd service file
nginx_conf=rdmo.conf                 # the nginx config file
certbot_email=admin@jochenklar.de    # the email to register certbot with
certbot_hostname=rdmo.jochenklar.de  # the hostname for the certificate
```

`local_py`, `fixtures`, `rdmo_service`, and `nginx_conf` are files, which should be placed in the `files` directory.

Usage
-----

```bash
./play.sh
```
