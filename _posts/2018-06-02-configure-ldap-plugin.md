---
title: Configure ldap plugin
date: 2018-06-02 00:00:00 Z
description: configure ldap plugin
---

The goal of the directory synchronization tool, also called LDAP connector, is to provide a way for a passbolt administrator to synchronize a list of groups and users, as well as the associated group memberships. 

<!--end excerpt-->


## Introduction

### What is it?

The goal of the directory synchronization tool, also called LDAP connector, is to provide a way for a passbolt administrator to synchronize a list of groups and users, as well as the associated group memberships. 


Currently the connector supports two types of directory: OpenLDAP and Microsoft Active Directory. In the future 
we will also support other non ldap based user directories such as Google API User Directory.


### How does it work?

In a nutshell this part of the application will try to keep passbolt and a directory in sync with a minimal 
involvement of the administrators and group managers. However if an action is not possible, such as, deleting 
a user that is the sole password owner, the process triggers will trigger relevant email notifications so 
that a human can solve it manually. An admin can also alternatively tell passbolt to ignore a record in the 
next synchronization round, if the issue does not need to be resolved.

### Requirements

The directory synchronization tools requires the [php-ldap extension](https://secure.php.net/manual/en/book.ldap.php)
to be present on the server. If you built your own server the way you install 
[php-ldap](https://packages.debian.org/stretch/php-ldap) will depend on your system flavor. 

On Debian using nginx for example you can do:
```bash
sudo apt-get install php-ldap 
sudo service nginx restart
```

Make sure the ldap extension is present in the php-cli.ini file. 
You should add `extension=ldap.so` if it is not already present:
```bash
$ php -i |grep php\.ini
Configuration File (php.ini) Path => /etc/php/7.0/cli
Loaded Configuration File => /etc/php/7.0/cli/php.ini
$ nano /etc/php/7.0/cli/php.ini
```

For testing purpose, it might be handy to have some [ldap utilities](https://wiki.debian.org/LDAP/LDAPUtils) 
installed on your system. On Debian you can use ldapsearch for example to search for and display entries:
```bash
sudo apt-get install ldap-utils
ldapsearch -b'dc=example,dc=com' -x
```

The plugin relies on a 3rd party library called ldaptools which you will need to install as part of your passbolt 
update or install. You can get it the same way than other php dependencies using composer:
```bash
cd /var/www/passbolt
git pull origin master
composer install
./bin/cake passbolt migrate
```

To run, the ldap plugin needs to have at least one active admin user existing inside passbolt.
