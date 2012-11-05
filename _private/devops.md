Setup Ubuntu server
===================

MongoDB
-------
[Install MongoDB on Ubuntu](http://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/)
* `apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10`
* `echo "deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen" >> /etc/apt/sources.list.d/10gen.list`
* `apt-get update`
* `apt-get install mongodb-10gen`
* TODO configure mongodb

Percona
-------
Install 5.5 from the [Percona apt Repository](http://www.percona.com/doc/percona-server/5.5/installation/apt_repo.html)
* `gpg --keyserver  hkp://keys.gnupg.net --recv-keys 1C4CBDCDCD2EFD2A`
* `gpg -a --export CD2EFD2A | apt-key add -`
* `echo "deb http://repo.percona.com/apt precise main" >> /etc/apt/sources.list.d/percona.list`
* `echo "deb-src http://repo.percona.com/apt precise main" >> /etc/apt/sources.list.d/percona.list`
* `apt-get update`
* `apt-get install percona-server-server-5.5 percona-server-client-5.5`
* `echo "Package: *" >> /etc/apt/preferences.d/00percona.pref`
* `echo "Pin: release o=Percona Development Team" >> /etc/apt/preferences.d/00percona.pref`
* `echo "Pin-Priority: 1001" >> /etc/apt/preferences.d/00percona.pref`

Nginx
-----
Install Nginx from their [Launchpad PPA](http://wiki.nginx.org/Install#Ubuntu_PPA) (Personal Package Archive)
* `apt-get install python-software-properties`
* `add-apt-repository ppa:nginx/(stable|development)`
* `apt-get update`
* `apt-get install nginx`


HSH server setup
================

Setting up a Ubuntu server from scratch:

- Start with a `apt-get update` and `apt-get dist-upgrade`
- [Install](http://wiki.nginx.org/Install#Ubuntu_PPA) Nginx from their Launchpad PPA (Personal Package Archive)
- [Install](http://www.percona.com/doc/percona-server/5.5/installation.html#using-percona-software-repositories?id=repositories:start)
Percona Server 5.5 from the [Percona apt repository](http://www.percona.com/doc/percona-server/5.5/installation/apt_repo.html) then configure users:
    - `CREATE USER ‘hshapi’@’localhost’ IDENTIFIED BY ‘hshapi’;`
    - `CREATE DATABASE hshapi;`
    - `GRANT ALL ON hshapi.* to ‘hshapi’@’localhost’;`
- Install git:
    - `apt-get install git`
    - Install [git-flow](https://github.com/nvie/gitflow)
        + `git clone --recursive git://github.com/nvie/gitflow.git`
        + `cd gitflow && sudo make install`
- Install Python 2.7
    - `apt-get install python2.7 python2.7-dev`
    - make <em>/usr/bin/python</em> point to 2.7 and update <em>/usr/share/python/debian\_defaults</em>
- [Install](http://www.pip-installer.org/en/latest/installing.html) pip (not from apt)
    - with a `pip install --upgrade pip virtualenv` for good measure
- Install libjpeg and libpng
    - Linux: `apt-get install libjpeg-dev libpng-dev`
    - OS X: use [these binaries](http://ethan.tira-thompson.com/Mac_OS_X_Ports.html)

