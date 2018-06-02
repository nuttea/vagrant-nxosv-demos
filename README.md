# Cisco NX-OSv Demos
This repository contains demos showing how automation tools can be used to manage Open NX-OS. These are based on the virtual Nexus 9000 and use Vagrant for provisioning the demo/test environments.
## Requirements
All of the demos assume the following requirements:

* Vagrant (tested on 2.1.1)
* VirtualBox (tested with 5.1.38)
* NX-OSv box added to your vagrant:
    * Download the .box file from [CCO]("https://software.cisco.com/download/home/286312239/type/282088129/release/7.0%25283%2529I5%25282%2529")
    * Add to vagrant: `vagrant box add --name nxosv/7-0-3-i5-2 nxosv-final.7.0.3.I5.2.box`
    * Verify: Run `vagrant box list` and look for `nxosv/7-0-3-i5-2                  (virtualbox, 0)`

## Available Demos
The following demos are currently available in this repository:

* **Ansible**: Sets up a Ansible master server and two virtual Nexus 9000 switches, each with the nxapi enabled and ready for Ansible master to run ansible playbook.
* Basic playbook
    * ssh to ansible master with `vagrant ssh master`
    * go to ansible directory `cd /vagrant/ansible`
    * run `ansible-playbook -i hosts sample-playbook.yml`. This will...
        * set default setting to interface Ethernet1/3 and Ethernet1/4
        * shutdown Ethernet1/3
        * set description and mode L3 to Ethernet1/4
* VXLAN MP-BGP EVPN Spines and Leafs playbook
    * ssh to ansible master with `vagrant ssh master`
    * go to ansible directory `cd /vagrant/ansible`
    * run `ansible-playbook -i hosts site.yml`
    * This will provisioning Spines and Leafs VXLAN EVPN based on tasks that defined by roles
