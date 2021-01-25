## What is Keycloak

- Single Sign On / Identity Management / Access Control solution
- Official Site[Keycloak.org](https://www.keycloak.org/)
- Japanese Document - [https://keycloak-documentation.openstandia.jp/](https://keycloak-documentation.openstandia.jp/)

## Quick Start

1. Create Keycloak admin user

```
$ sudo /opt/keycloak/bin/add-user-keycloak.sh -r master -u kcadmin -p Kcp@ss
Added 'kcadmin' to '/opt/keycloak/standalone/configuration/keycloak-add-user.json', restart server to load user
```

2.Run keycloak as standalone mode

```
$ sudo -u keycloak /opt/keycloak/bin/standalone.sh
```

3. Add entry to hosts file on your mother box

```
192.168.56.67  kc.ad.example.com
```

( The IP address depends on your virtual machine settings )

3. Log in to admin console at [http://kc.ad.example.com/auth/admin/](http://kc.ad.example.com/auth/admin/)

See /etc/nginx/conf.d/keycloak.conf for details.

