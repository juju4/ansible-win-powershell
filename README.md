[![Build Status - Master](https://travis-ci.org/juju4/ansible-win-powershell.svg?branch=master)](https://travis-ci.org/juju4/ansible-win-powershell)
[![Build Status - Devel](https://travis-ci.org/juju4/ansible-win-powershell.svg?branch=devel)](https://travis-ci.org/juju4/ansible-win-powershell/branches)(Syntax Only)

[![Appveyor - Master](https://ci.appveyor.com/api/projects/status/1033u05y7ymce0w5?svg=true)](https://ci.appveyor.com/project/juju4/ansible-win-powershell)
![Appveyor - Devel](https://ci.appveyor.com/api/projects/status/1033u05y7ymce0w5/branch/devel?svg=true)

# Windows firewall ansible role

Ansible role to setup powershell security on Windows system (logging, profile...).

## Requirements & Dependencies

### Ansible
It was tested on the following versions:
 * 2.4 (required since s/include:/include_tasks:/)

### Operating systems

Tested in Appveyor

## Example Playbook

Just include this role in your list.
For example

```
- host: all
  roles:
    - juju4.win-powershell
```

Run
```
$ ansible -i inventory -m win_ping win --ask-pass
$ ansible-playbook -i inventory --limit win site.yml
```

## Variables

See defaults/main.yml for full scope

## Continuous integration

This role has a travis basic test (for github, syntax check only), Appveyor test and a Vagrantfile (test/vagrant).

```
$ cd /path/to/roles/juju4.win-powershell/test/vagrant
$ vagrant up
$ vagrant provision
$ vagrant destroy
$ ansible -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory -m win_ping -e ansible_winrm_server_cert_validation=ignore -e ansible_ssh_port=55986 all
```

## Troubleshooting & Known issues

## FAQ

## License

BSD 2-clause

