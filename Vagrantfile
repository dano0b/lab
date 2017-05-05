# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

ENV["LC_ALL"] = "en_US.UTF-8"
ENV["TZ"] = "Europe/Berlin"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "centos/7"

    config.vm.provider :kvm do |kvm, override|
        kvm.memory_size     = '2048m'
    #config.vm.provider "virtualbox" do |v|
       # v.memory = 2048
    end
    config.hostmanager.enabled = true
    config.hostmanager.manage_host = true
    config.hostmanager.manage_guest = true
    config.hostmanager.ignore_private_ip = false
    config.hostmanager.include_offline = true
	(1..3).each do |i|
        config.vm.define "node-#{i}" do |node|
            node.vm.provision "ansible" do |ansible|
                ansible.playbook = "provision.yml"
            end
        end
    end
end
