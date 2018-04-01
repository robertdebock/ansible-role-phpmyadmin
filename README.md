php
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-php.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-php)

Provides PHP for your system.

Context
--------
This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/robertdebock.github.io/artifacts/phpmyadmin.png "Dependency")

Requirements
------------

Access to a repository containing packages, likely on the internet. PHP, Apache HTTPD and MySQL should be available.

Role Variables
--------------

None known

Dependencies
------------

These are suggested roles to prepare your system.

- robertdebock.bootstrap
- robertdebock.httpd
- robertdebock.mysql
- robertdebock.php

Download the dependencies by issuing this command:
```
ansible-galaxy install --role-file requirements.yml
```

Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.3|ansible 2.4|ansible 2.5|
|------------|-----------|-----------|-----------|
|alpine-3.5|no|no|no|
|alpine-3.6|no|no|no
|archlinux|no|yes|yes|
|centos-6|no|no|no|
|centos-7|no|no|no|
|debian-buster|no|no|no|
|debian-jessie|no|no|no|
|debian-sid|no|yes|yes|
|debian-stretch|no|yes|yes|
|fedora-26|no|yes|yes|
|fedora-27|no|yes|yes|
|opensuse-42.2|no|yes|yes|
|opensuse-42.3|no|yes|yes|
|ubuntu-artful|no|yes|yes|
|ubuntu-trusty|no|no|no|
|ubuntu-xenial|no|yes|yes|

Example Playbook
----------------

```
- hosts: servers

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.httpd
    - role: robertdebock.php
    - role: robertdebock.mysql
    - role: robertdebock.phpmyadmin
```

Install this role using `galaxy install robertdebock.phpmyadmin`.

License
-------

Apache License, Version 2.0

Author Information
------------------

Robert de Bock <robert@meinit.nl>
