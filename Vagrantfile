# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

ENV["LC_ALL"] = "en_US.UTF-8"
ENV["TZ"] = "Europe/Berlin"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.hostmanager.enabled = true
    config.hostmanager.manage_host = true
    config.hostmanager.manage_guest = true
    config.hostmanager.ignore_private_ip = false
    config.hostmanager.include_offline = true

    config.vm.box = "centos/7"

    config.vm.provider :libvirt do |domain|
        domain.memory = '1024m'
    end

	(1..3).each do |i|
        config.vm.define "frontend-#{i}" do |node|
            node.vm.provision "ansible" do |ansible|
                ansible.playbook = "provision.yml"
            end
        end
    end
	(1..3).each do |i|
        config.vm.define "backend-#{i}" do |node|
            node.vm.provision "ansible" do |ansible|
                ansible.playbook = "provision.yml"
            end
        end
    end

end
