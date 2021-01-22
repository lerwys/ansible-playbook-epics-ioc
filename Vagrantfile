# -*- mode: ruby -*-
# vi: set ft=ruby :

hosts = {
  "debian.jessie"  => "192.168.33.10",
  "debian.stretch" => "192.168.33.11",
  "debian.buster"  => "192.168.33.12",
  "ubuntu.trusty"  => "192.168.33.13",
  "ubuntu.xenial"  => "192.168.33.14",
  "centos.7"  => "192.168.33.15",
  "centos.8"  => "192.168.33.16",
}

Vagrant.configure("2") do |config|
  hosts.each do |name, ip|
    config.vm.define name do |machine|
      if name.eql? "debian.jessie" then
        machine.vm.box = "debian/jessie64"
      elsif name.eql? "debian.stretch" then
        machine.vm.box = "debian/stretch64"
      elsif name.eql? "debian.buster" then
        machine.vm.box = "debian/buster64"
      elsif name.eql? "ubuntu.xenial" then
        machine.vm.box = "ubuntu/xenial64"
      elsif name.eql? "ubuntu.trusty" then
        machine.vm.box = "ubuntu/trusty64"
      elsif name.eql? "centos.7" then
        machine.vm.box = "centos/7"
      elsif name.eql? "centos.8" then
        machine.vm.box = "centos/8"
      end
      machine.vm.hostname = "%s" % name
      machine.vm.network :private_network, ip: ip
      machine.vm.provider "virtualbox" do |v|
          v.name = name
          v.customize ["modifyvm", :id, "--memory", 256]
      end
      machine.vm.provider :libvirt do |v|
        v.qemu_use_session = false
      end
    end
  end
end
