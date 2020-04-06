# phpmyadmin

Install and configure phpmyadmin on your system.

|Travis|GitHub|Quality|Downloads|
|------|------|-------|---------|
|[![travis](https://travis-ci.com/robertdebock/ansible-role-phpmyadmin.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-phpmyadmin)|[![github](https://github.com/robertdebock/ansible-role-phpmyadmin/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-phpmyadmin/actions)|[![quality](https://img.shields.io/ansible/quality/23499)](https://galaxy.ansible.com/robertdebock/phpmyadmin)|[![downloads](https://img.shields.io/ansible/role/d/23499)](https://galaxy.ansible.com/robertdebock/phpmyadmin)|

## Example Playbook

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: robertdebock.httpd
    - role: robertdebock.phpmyadmin
```

The machine may need to be prepared using `molecule/resources/prepare.yml`:
```yaml
---
- name: Prepare
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.core_dependencies
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

For verification `molecule/resources/verify.yml` run after the role has been applied.
```yaml
---
- name: Verify
  hosts: all
  become: yes
  gather_facts: yes

  tasks:
    - name: check if connection still works
      ping:
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## Role Variables

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

## Requirements

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- robertdebock.bootstrap
- robertdebock.buildtools
- robertdebock.core_dependencies
- robertdebock.epel
- robertdebock.python_pip
- robertdebock.httpd
- robertdebock.php
- robertdebock.mysql
- robertdebock.remi

```

## Dependencies

Most roles require some kind of preparation, this is done in `molecule/default/prepare.yml`. This role has a "hard" dependency on the following roles:

- robertdebock.httpd
## Context

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/phpmyadmin.png "Dependency")

## Compatibility

This role has been tested on these [container images](https://hub.docker.com/):

|container|tags|
|---------|----|
|debian|all|
|el|8|
|fedora|all|
|opensuse|all|
|ubuntu|bionic|

The minimum version of Ansible required is 2.8 but tests have been done to:

- The previous version, on version lower.
- The current version.
- The development version.

## Exceptions

Some variarations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| Alpine | php-pecl-zip (missing) |
| amazonlinux | Dependency (python_pip) not available |

## Included version(s)

This role [refers to a version](https://github.com/robertdebock/ansible-role-phpmyadmin/blob/master/defaults/main.yml) released by phpMyAdmin. Check the released version(s) here:
- [phpmyadmin](https://www.phpmyadmin.net/downloads/).

This version reference means a role may get outdated. Monthly tests occur to see if [bit-rot](https://en.wikipedia.org/wiki/Software_rot) occured. If you however find a problem, please create an issue, I'll get on it as soon as possible.
## Testing

[Unit tests](https://travis-ci.com/robertdebock/ansible-role-phpmyadmin) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-phpmyadmin/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

## License

Apache-2.0


## Author Information

[Robert de Bock](https://robertdebock.nl/)
