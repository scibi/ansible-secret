## [![DebOps project](http://debops.org/images/debops-small.png)](http://debops.org) secret

[![Travis CI](http://img.shields.io/travis/debops/ansible-secret.svg?style=flat)](http://travis-ci.org/debops/ansible-secret) [![test-suite](http://img.shields.io/badge/test--suite-ansible--secret-blue.svg?style=flat)](https://github.com/debops/test-suite/tree/master/ansible-secret/)  [![Ansible Galaxy](http://img.shields.io/badge/galaxy-debops.secret-660198.svg?style=flat)](https://galaxy.ansible.com/list#/roles/1598)

This role enables you to have a separate directory on Ansible Controller
(different than the playbook directory and inventory directory) which can be
used as a handy "workspace" for other roles.

Some usage examples of this role in [DebOps](http://debops.org/) include:

- password lookups, either from current role, or using known location of
  passwords from other roles, usually dependencies (for example
  `debops.mysql` role can manage an user account in the database with
  random password and other role can lookup that password to include in
  a generated configuration file);

- secure file storage, for example for application keys generated on remote
  hosts (`debops.boxbackup` role retrieves client keys for backup
  purposes), for that reason secret directory should be protected by an
  external means, for example encrypted filesystem (currently there is no
  encryption provided by default);

- secure workspace (`debops.boxbackup` role, again, uses secret directory
  to create and manage Root CA for backup servers - client and server
  certificates are automatically downloaded to Ansible Controller, signed
  and uploaded to destination hosts);

- simple centralized backup (specific roles like `sshd`, `pki` and
  `monkeysphere` have a separate task lists that are invoked by custom
  playbooks to allow backup and restoration of ssh host keys and SSL
  certificates. Generated .tar.gz files are kept on Ansible Controller in
  secret directory).

### Installation

This role requires at least Ansible `v1.7.0`. To install it, run:

    ansible-galaxy install debops.secret

### Documentation

More information about `debops.secret` can be found in the
[official debops.secret documentation](http://docs.debops.org/en/latest/ansible/roles/debops.secret.html).



### Are you using this as a standalone role without DebOps?

You may need to include missing roles from the [DebOps common
playbook](https://github.com/debops/debops-playbooks/blob/master/playbooks/common.yml)
into your playbook.

[Try DebOps now](https://github.com/debops/debops) for a complete solution to run your Debian-based infrastructure.





### Authors and license

`secret` role was written by:
- Maciej Delmanowski | [e-mail](mailto:drybjed@gmail.com) | [Twitter](https://twitter.com/drybjed) | [GitHub](https://github.com/drybjed)

License: [GPLv3](https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29)

***

This role is part of the [DebOps](http://debops.org/) project. README generated by [ansigenome](https://github.com/nickjj/ansigenome/).