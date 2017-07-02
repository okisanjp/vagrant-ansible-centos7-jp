# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
SYNC_FOLDER_LOCAL = "~/workspace"
SYNC_FOLDER_VM = "/var/www"
VM_NETWORK_PRIVATE_IP = "192.168.33.10"
VM_HOSTNAME = "localvm"
VM_BOX = "bento/centos-7.2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.hostname = VM_HOSTNAME
    config.vm.box = VM_BOX
    config.vm.network "private_network", ip: VM_NETWORK_PRIVATE_IP
    config.vm.synced_folder SYNC_FOLDER_LOCAL, SYNC_FOLDER_VM
    config.ssh.forward_agent = true

    config.vm.provider "virtualbox" do |virtualbox|
        virtualbox.customize ["modifyvm", :id, "--memory", "4096"]
        virtualbox.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
        virtualbox.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end

    config.vm.provision "ansible" do |ansible|
        ansible.limit = 'all'
        ansible.playbook = "ansible/provision.yml"
        ansible.inventory_path = "ansible/hosts"
    end
end
