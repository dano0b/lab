# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    amountNodes = 3

    config.landrush.enabled = true
    config.landrush.tld = "lab"

    config.vm.box = "centos/7"

    config.vm.provider :libvirt do |vm|
        vm.memory = '1024m'
    end

	(1..amountNodes).each do |id|
        config.vm.define "node-#{id}" do |node|
            node.vm.hostname = "node-#{id}.lab"
            node.vm.provision "ansible" do |ansible|
                ansible.playbook = "provision.yml"
            end
        end
    end
end
