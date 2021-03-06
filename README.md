
# Vagrant and RHEL
This project is used for standing up a vagrant box running RHEL  quickly and consistently using the setup.sh to provision the box.  I've included a packer build script for reference,  you can download the latest RHEL vagrant box for virtualbox and libvirt from jasonhorn/rhel7 which is also referenced in the included Vagrantfile.

## Pre-Reqs
Vagrant and Virtualbox or libivrt for provisioning need to be installed with a valid RHSM account.  This Vagrant box will attempt to register with RedHat and expects the following variables be exported in your environment.
```
export SUB_USER=< rhsm_username >
export SUB_PASS=< rhsm_password >
export POOLID=< pool id to attach >
```

### Vagrant
Vagrant installers [vagrantup.com](https://www.vagrantup.com/downloads.html) 

### Vagrant libvirt
https://github.com/vagrant-libvirt/vagrant-libvirt

## Vagrantfile
Customization of the Vagrantfile is always encouraged,  by default the following is set.
``` 
static_ip = '192.168.110.230'
private_key = '~/.ssh/id_rsa'
boxes = [
{
:name => "rhel7-test",
:eth1 => static_ip,
:mem => "6144",
:vcpu => "1",
:default => true,
:share => "/vagrant",         # directory to present share of host machine on VM
:localdir => "~/projects",  # directory to share on host machine
:port => "9443",
:box => "jasonhorn/rhel7",
}
]
```

## Setup 
The setup.sh script is provided as reference and is used to keep a consistent creation of aliases, packages and configurations.

## Deploy
```
git clone https://github.com/hornjason/vagrant-rhel
cd vagrant-rhel
vagrant up
vagrant ssh
```
