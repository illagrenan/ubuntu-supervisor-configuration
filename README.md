# ubuntu-supervisor-configuration

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

```bash
mkdir -p /etc/supervisor/
sudo curl https://raw.githubusercontent.com/illagrenan/ubuntu-supervisor-configuration/master/supervisord.conf > /etc/supervisor/supervisord.conf
```

If you want your custom configuration, use built-in command:

```bash
echo_supervisord_conf > /etc/supervisord.conf
```

6) Use it:

```bash
service supervisor stop
service supervisor start
```

## Resources

* http://serverfault.com/a/96500/100080
* https://github.com/Supervisor/initscripts/blob/master/ubuntu
