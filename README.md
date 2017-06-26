# Tutorial how to install Supervisor on Ubuntu 14.04/16.04 (LTS versions) using pip

[![Build Status](https://travis-ci.org/illagrenan/ubuntu-supervisor-configuration.svg?branch=master)](https://travis-ci.org/illagrenan/ubuntu-supervisor-configuration)

**1) Install pip and supervisor:**

```bash
[sudo] pip install --upgrade pip
sudo pip install --upgrade supervisor
```

**2) Add init script from this repository:**

```bash
sudo curl https://raw.githubusercontent.com/illagrenan/ubuntu-supervisor-configuration/master/supervisor.sh > /etc/init.d/supervisor
```
:bulb: Before executing this command, you should [review `supervisor.sh`](https://github.com/illagrenan/ubuntu-supervisor-configuration/blob/master/supervisor.sh)

**3) Add *‚execute‘* permission:**

```bash
sudo chmod +x /etc/init.d/supervisor
```

**4) Schedule:**

```bash
sudo update-rc.d supervisor defaults
```

**5) Create main configuration file**

You have two options: **5A)** Use configuration [file from this repository](https://github.com/illagrenan/ubuntu-supervisor-configuration/blob/master/supervisord.conf) *OR* **5B)** Use [standard supervisor configuration file](http://supervisord.org/installing.html#creating-a-configuration-file).

**5A)**

Do not forget to **follow** steps 6)+7)

```bash
mkdir -p /etc/supervisor/
sudo curl https://raw.githubusercontent.com/illagrenan/ubuntu-supervisor-configuration/master/supervisord.conf > /etc/supervisor/supervisord.conf
```

**5B)**

**Skip** steps 6)+7)

```bash
echo_supervisord_conf > /etc/supervisord.conf
```

**(only for 5A) 6) Create log and conf directories:**

```bash
mkdir -p /var/log/supervisor
mkdir -p /etc/supervisor/conf.d/
```

**(only for 5A) 7) Create new group:**

See `chown=root:supervisor` in configuration.

```bash
groupadd supervisor
```

**8) Fix supervisorctl**

More info here: http://stackoverflow.com/a/17036409/752142

```bash
ln -s /etc/supervisor/supervisord.conf /etc/supervisord.conf
```

**9) Use it:**

```bash
service supervisor stop
service supervisor start
```

## Resources

* [Supervisor homepage and docs](http://supervisord.org/)
* [http://serverfault.com/a/96500/100080](http://serverfault.com/a/96500/100080)
* [https://github.com/Supervisor/initscripts/blob/master/ubuntu](https://github.com/Supervisor/initscripts/blob/master/ubuntu)
