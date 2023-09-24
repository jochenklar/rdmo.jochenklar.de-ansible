rdmo.jochenklar.de-ansible
==========================

The ansible playbook to deploy <https://rdmo.jochenklar.de>.

It can be reused to deploy other instances of [RDMO](https://rdmorganiser.github.io) (with PostgresSQL and Gunicorn).

Please also note <https://github.com/rdmorganiser/rdmo-ansible> for a different approach.


Setup
-----

Create a `hosts` file with the hostname of your RDMO machine and the following variables:

```plain
[rdmo]
rdmo.jochenklar.de                   # the hostname for ansible

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
