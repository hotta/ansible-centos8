This set of ansible playbooks derived from [ansible-centos7](https://github.com/hotta/ansible-centos7) deploy various environment such as laravel / IBM MQ / Radius / WordPress etc. on CentOS 8.x. It is intended to run at each host to provision the localhost itself. Provisioning remote hosts are not tested.

This is alfa vervion so you should not use it ;-)

## Prerequisite(Test Environment)

- Vagrant + VirtualBox VM running CentOS 8.2 with git and ansible 2.9.x.
- typical installation process could be like this:

```bash
mkdir XXXX
cd XXXXX
vi Vagrantfile (See below.)
vagrant up
```
And then log in to the VM as user "vagrant".

### Sample Vagrantfile:

```Vagrantfile
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/centos8"
  config.vm.network "private_network", ip: "192.168.56.2"
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.hostname = "example.local"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end
  config.vm.provision "shell", inline: <<-SHELL
		sudo dnf -y update
    sudo dnf -y install git epel-release
    sudo dnf -y install ansible
		ansible-galaxy collection install community.mysql
  SHELL
end
```

## Put this set of playbooks

```bash
$ git clone https://github.com/hotta/ansible-centos8.git
```

## (Option) Customize localhost.yml 

Take a glance at group_vars/all first. If you'd like to customize any variable, you can override it by write down in host_vars/localhost.yml.

Especially, if you prefer to use CentOS Stream 8, set ENABLE_STREAM to true here.
```bash
$ cd host_vars
$ cp localhost.yml.tmpl localhost.yml
$ vi localhost.yml
$ cd ..
```

## Building environment 

```bash
$ ansible-playbook jobs/JOB-NAME-YOU-WANT-TO-DEPLOY.yml
```

## Components versions

### tested ( as of 2020/12/08 ).

- nothing :-)
