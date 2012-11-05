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

