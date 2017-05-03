# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANT_BOX = "ubuntu-xenial64-docker"
NODE_COUNT = 2

Vagrant.configure("2") do |config|
    config.vm.define "master" do |m|
        m.vm.box = VAGRANT_BOX
        m.vm.network :private_network, ip: "172.20.2.30"
        m.vm.hostname = "master.docker.test"
        m.vm.provider "virtualbox" do |v|
            v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
            v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
            v.memory = 512
        end
        m.vm.synced_folder ".", "/vagrant", type: "virtualbox"
	    m.ssh.username = "ubuntu"
    end
    (1..NODE_COUNT).each do |i|
        config.vm.define "slave0#{i}" do |sub|
            sub.vm.box = VAGRANT_BOX
            sub.vm.network :private_network, ip: "172.20.2.#{60 + i}"
            sub.vm.hostname = "slave0#{i}.docker.test"
            sub.vm.provider "virtualbox" do |v|
                v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
                v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
                v.memory = 512
            end
            sub.vm.synced_folder ".", "/vagrant", type: "virtualbox"
            sub.ssh.username = "ubuntu"
        end
    end
end
