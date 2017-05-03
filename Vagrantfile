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
        end
        m.vm.synced_folder ".", "/vagrant", type: "virtualbox"
	    m.ssh.username = "ubuntu"
    end
    config.vm.define "slave01" do |s|
        s.vm.box = VAGRANT_BOX
        s.vm.network :private_network, ip: "172.20.2.31"
        s.vm.hostname = "slave01.docker.test"
        s.vm.provider "virtualbox" do |v|
            v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
            v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
        end
        s.vm.synced_folder ".", "/vagrant", type: "virtualbox"
	    s.ssh.username = "ubuntu"
    end
    config.vm.define "slave02" do |s|
        s.vm.box = VAGRANT_BOX
        s.vm.network :private_network, ip: "172.20.2.32"
        s.vm.hostname = "slave02.docker.test"
        s.vm.provider "virtualbox" do |v|
            v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
            v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
        end
        s.vm.synced_folder ".", "/vagrant", type: "virtualbox"
	    s.ssh.username = "ubuntu"
    end
end
