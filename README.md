phpmyadmin
=========

<img src="https://docs.ansible.com/ansible-tower/3.2.4/html_ja/installandreference/_static/images/logo_invert.png" width="10%" height="10%" alt="Ansible logo" align="right"/>
<a href="https://travis-ci.org/robertdebock/ansible-role-phpmyadmin"><img src="https://travis-ci.org/robertdebock/ansible-role-phpmyadmin.svg?branch=master" alt="Build status" align="left"/></a>

Install and configure phpmyadmin on your system.

Example Playbook
----------------

This example is taken from `molecule/resources/playbook.yml`:
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - robertdebock.httpd
    - robertdebock.phpmyadmin
```

The machine you are running this on, may need to be prepared.
```yaml
---
- name: Prepare
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.buildtools
    - role: robertdebock.epel
    - role: robertdebock.python_pip
      python_pip_modules:
        - name: pyopenssl
    - role: robertdebock.httpd
    - role: robertdebock.mysql
    - role: robertdebock.remi
      remi_enabled_repositories:
        - php73
    - role: robertdebock.php
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

Role Variables
--------------

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for phpmyadmin

# The version of PHPMyAdmin to install
phpmyadmin_version: 4.9.0.1

# Where to connect to for the database.
phpmyadmin_database_host: localhost

# To authenticate to the database using a user/pass requested in the browser,
# ensure you set phpmyadmin_blowfish_secret.
phpmyadmin_blowfish_secret: x7GD9DBEE32bAWd2sTHKBfYiqOfnj82neaPD3wrDTs0K

# Only set these (and unset phpmyadmin_blowfish_secret) to save the login
# credentials in the configuration file.
phpmyadmin_database_user: root
phpmyadmin_database_pass: root

phpmyadmin_database_compress: false
phpmyadmin_database_allownopassword: false
```

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- robertdebock.bootstrap
- robertdebock.buildtools
- robertdebock.epel
- robertdebock.python_pip
- robertdebock.httpd
- robertdebock.php
- robertdebock.mysql
- robertdebock.remi

```

This role uses the following modules:
```yaml
---
- file
- package
- template
- unarchive
```

Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/phpmyadmin.png "Dependency")


Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.7|ansible 2.8|ansible devel|
|------------|-----------|-----------|-------------|
|alpine-edge*|no|no|no*|
|alpine-latest|no|no|no*|
|archlinux|yes|yes|yes*|
|centos-6|no|no|no*|
|centos-latest|yes|yes|yes*|
|debian-stable|yes|yes|yes*|
|debian-unstable*|yes|yes|yes*|
|fedora-latest|yes|yes|yes*|
|fedora-rawhide*|yes|yes|yes*|
|opensuse-leap|yes|yes|yes*|
|ubuntu-devel*|yes|yes|yes*|
|ubuntu-latest|yes|yes|yes*|
|ubuntu-rolling|yes|yes|yes*|

A single star means the build may fail, it's marked as an experimental build.


Included version(s)
-------------------

This role [refers to a version](https://github.com/robertdebock/ansible-role-phpmyadmin/blob/master/defaults/main.yml) released by phpMyAdmin. Check the released version(s) here:
- [phpmyadmin](https://www.phpmyadmin.net/downloads/).

This version reference means a role may get outdated. Monthly tests occur to see if [bit-rot](https://en.wikipedia.org/wiki/Software_rot) occured. If you however find a problem, please create an issue, I'll get on it as soon as possible.

Testing
-------

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-phpmyadmin) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-phpmyadmin/issues)

To test this role locally please use [Molecule](https://github.com/ansible/molecule):
```
pip install molecule
molecule test
```

To test on Amazon EC2, configure [~/.aws/credentials](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html) and set a region using `export AWS_REGION=eu-central-1` before running `molecule test --scenario-name ec2`.

There are many specific scenarios available, please have a look in the `molecule/` directory.

License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl/)
