phpmyadmin
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-php.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-php)

Provides PHPMyAdmin for your system.

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-phpmyadmin) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-phpmyadmin/issues)

To test this role locally please use [Molecule](https://github.com/metacloud/molecule):
```
pip install molecule
molecule test
```
There are many scenarios available, please have a look in the `molecule/` directory.

Context
--------
This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/phpmyadmin.png "Dependency")

Requirements
------------

Access to a repository containing packages, likely on the internet. PHP, Apache HTTPD and MySQL should be available.

Role Variables
--------------

Default values can be found in default/main.yml.

- phpmyadmin_version
- phpmyadmin_database_host
- phpmyadmin_blowfish_secret
- phpmyadmin_database_user
- phpmyadmin_database_pass
- phpmyadmin_database_compress
- phpmyadmin_database_allownopassword

Dependencies
------------

These are suggested roles to prepare your system.

- [robertdebock.bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap/)
- [robertdebock.buildtools](https://galaxy.ansible.com/robertdebock/buildtools/)
- [robertdebock.epel](https://galaxy.ansible.com/robertdebock/epel/)
- [robertdebock.httpd](https://galaxy.ansible.com/robertdebock/httpd/)
- [robertdebock.mysql](https://galaxy.ansible.com/robertdebock/mysql/)
- [robertdebock.php](https://galaxy.ansible.com/robertdebock/php/)
- [robertdebock.python_pip](https://galaxy.ansible.com/robertdebock/python_pip/)

Download the dependencies by issuing this command:
```
ansible-galaxy install --role-file requirements.yml
```

Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.4|ansible 2.5|ansible 2.6|ansible 2.7|ansible devel|
|------------|-----------|-----------|-----------|-----------|-------------|
|alpine-edge*|yes|yes|yes|yes|yes*|
|alpine-latest|no|no|no|no|yes*|
|archlinux|yes|yes|yes|yes|yes*|
|centos-6|no|no|no|no|yes*|
|centos-latest|no|no|no|no|yes*|
|debian-latest|yes|yes|yes|yes|yes*|
|debian-stable|yes|yes|yes|yes|yes*|
|debian-unstable*|yes|yes|yes|yes|yes*|
|fedora-latest|yes|yes|yes|yes|yes*|
|fedora-rawhide*|yes|yes|yes|yes|yes*|
|opensuse-leap|yes|yes|yes|yes|yes*|
|opensuse-tumbleweed|yes|yes|yes|yes|yes*|
|ubuntu-artful|yes|yes|yes|yes|yes*|
|ubuntu-devel*|yes|yes|yes|yes|yes*|
|ubuntu-latest|yes|yes|yes|yes|yes*|

A single star means the build may fail, it's marked as an experimental build.

Example Playbook
----------------

```
- hosts: servers

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.epel
    - role: robertdebock.python_pip
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

[Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
