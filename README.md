# OpenLocalization Vagrant

A virtual machine powered by [Vagrant](https://www.vagrantup.com/) and provionned
via [Ansible](http://www.ansible.com/), to easily install OpenLocalization app.

## Requirements

- Install [Vagrant](https://www.vagrantup.com/downloads.html).
- Install [Ansible](http://docs.ansible.com/intro_installation.html).

## Installation

First fetch the [openl10n](https://github.com/openl10n/openl10n) repository via git:

```shell
git clone https://github.com/openl10n/openl10n.git
```

Or if you already have cloned it, just create the link to the correct location:

```shell
ln -s ../openl10n openl10n
```

Then launch the virtual machine via Vagrant:

```shell
vagrant up
```

To configure application, log in the virtual machine and go to the project root:

```shell
vagrant ssh
cd /var/www/openl10n.dev/current
vim app/config/parameters.yml
composer install
```

Finally, edit your `/etc/hosts` to use the correct hostname:

```
# /etc/hosts
10.0.0.42 openl10n.dev
```
