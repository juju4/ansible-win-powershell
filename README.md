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

* Pay attention to [Powershell v6 Core](http://www.labofapenetrationtester.com/2018/01/powershell6.html)! Not covered currently.

* Don't use constrained mode or test appropriately as it will likely break ansible and most powershell dependencies.

* Reference links
  * PowerShell5, WMF5. regedit or GPO. https://www.fireeye.com/blog/threat-research/2016/02/greater_visibilityt.html
  * https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/
  * https://www.blackhat.com/docs/us-14/materials/us-14-Kazanciyan-Investigating-Powershell-Attacks-WP.pdf
  * http://fr.slideshare.net/Hackerhurricane/ask-aalware-archaeologist/25
  * http://www.asd.gov.au/publications/protect/securing-powershell.htm
  * https://www.leeholmes.com/blog/2017/03/17/detecting-and-preventing-powershell-downgrade-attacks/
  * https://blogs.msdn.microsoft.com/daviddasneves/2017/05/25/powershell-security-at-enterprise-customers/
  * https://www.trendmicro.com/vinfo/us/security/news/security-technology/security-101-the-rise-of-fileless-threats-that-abuse-powershell
  * Forward EID 4104 to SIEM at least. https://msdn.microsoft.com/en-us/library/cc748890.aspx
  * https://media.defcon.org/DEF%20CON%2025/DEF%20CON%2025%20presentations/DEFCON-25-Daniel-Bohannon-and-Lee-Holmes-Revoke-Obfuscation.pdf
  * https://dfir.it/blog/2018/05/08/down-the-rabbit-hole-with-packaged-powershell-scripts/

## License

BSD 2-clause

