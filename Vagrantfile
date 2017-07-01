# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
SYNC_FOLDER_LOCAL = "~/workspace"
SYNC_FOLDER_VM = "/var/www"
VM_NETWORK_PRIVATE_IP = "192.168.33.10"
VM_HOSTNAME = "centos7.1"
VM_BOXNAME = "centos7.1"
VM_BOX_URL = "https://github.com/holms/vagrant-centos7-box/releases/download/7.1.1503.001/CentOS-7.1.1503-x86_64-netboot.box"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.hostname = VM_HOSTNAME
    config.vm.box = VM_BOXNAME
    config.vm.box_url = VM_BOX_URL
    config.vm.network "private_network", ip: VM_NETWORK_PRIVATE_IP
    config.vm.synced_folder SYNC_FOLDER_LOCAL, SYNC_FOLDER_VM
    config.ssh.forward_agent = true

    config.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--memory", "4096"]
        vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
        vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end
end
