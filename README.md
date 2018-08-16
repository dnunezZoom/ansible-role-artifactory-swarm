# artifactory-swarm

[![Build Status](https://travis-ci.org/inhumantsar/ansible-role-artifactory.svg?branch=master)](https://travis-ci.org/inhumantsar/ansible-role-artifactory)

Launches Artifactory on Docker Swarm

## Requirements

The target host must have Docker installed with Swarm initialized.

## Supported Platforms

* RHEL / CentOS: 6, 7      
* Fedora: 24-28      
* Debian:
    - jesse
    - sid
    - stretch
    - buster      
* Ubuntu
    - bionic
    - artful
    - zesty
    - yakkety
    - xenial
* Alpine

## Variables & Defaults

The defaults are fine if you're just trying things out. When moving into production though, you'll want to change `artifactory_postgres_user` & `artifactory_postgres_pass`.

If you're using an automatic proxy like [`jwilder/nginx-proxy`](https://github.com/jwilder/nginx-proxy) then you will also want to change `artifactory_deploy_labels`.

See [`defaults/main.yml`](defaults/main.yml) for more information.

## Usage

```
- hosts: localhost
  connection: local
  roles:
    - inhumantasr/artifactory_swarm
```

This stack includes a proxy which does redirects to whatever port the proxy is bound to. The default is `8082`. Putting another proxy in front of this is untested and could cause problems. Also, this proxy *does not* terminate SSL.


### Removing the stack

Set `artifactory_remove` to true and run the playbook. eg: `ansible-playbook ... -e artifactory_remove=true myplaybook.yml`

## Dependencies

None

## License
[BSD](LICENSE)

## Authors
[Shaun Martin](https://github.com/inhumantsar)