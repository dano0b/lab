# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    amountFrontendNodes = 3
    amountBackendNodes = 3

    config.landrush.enabled = true
    config.landrush.tld = "lab"

    config.vm.box = "centos/7"

    config.vm.provider :libvirt do |vm|
        vm.memory = '1024m'
    end

	(1..amountFrontendNodes).each do |id|
        config.vm.define "frontend-#{id}" do |node|
            node.vm.hostname = "frontend-#{id}.lab"
            node.vm.provision "ansible" do |ansible|
                ansible.playbook = "provision.yml"
            end
        end
    end
	(1..amountBackendNodes).each do |id|
        config.vm.define "backend-#{id}" do |node|
            node.vm.hostname = "backend-#{id}.lab"
            node.vm.provision "ansible" do |ansible|
                ansible.playbook = "provision.yml"
            end
        end
    end

end
