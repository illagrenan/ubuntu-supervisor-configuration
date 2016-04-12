# Supervisor on Ubuntu 14.04 installed by pip

[![Build Status](https://travis-ci.org/illagrenan/ubuntu-supervisor-configuration.svg?branch=master)](https://travis-ci.org/illagrenan/ubuntu-supervisor-configuration)

1) Install supervisor:

```bash
easy_install --upgrade pip
sudo pip install supervisor
```

2) Add init script:
```bash
sudo curl https://raw.githubusercontent.com/illagrenan/ubuntu-supervisor-configuration/master/supervisor.sh > /etc/init.d/supervisor
```

3) Fix permissions:

```bash
sudo chmod +x /etc/init.d/supervisor
```

4) Schedule:

```bash
sudo update-rc.d supervisor defaults
```

5) Write example configuration

If you use this configuration, follow steps 6)+7)

```bash
mkdir -p /etc/supervisor/
sudo curl https://raw.githubusercontent.com/illagrenan/ubuntu-supervisor-configuration/master/supervisord.conf > /etc/supervisor/supervisord.conf
```

If you want your custom configuration, use built-in command and skip steps 6)+7)

```bash
echo_supervisord_conf > /etc/supervisord.conf
```

6) Create log directory:

```bash
mkdir -p /var/log/supervisor
```

7) Create new group:

See `chown=root:supervisor` in configuration.

```bash
groupadd supervisor
```

8) Use it:

```bash
service supervisor stop
service supervisor start
```

## Resources

* http://serverfault.com/a/96500/100080
* https://github.com/Supervisor/initscripts/blob/master/ubuntu
