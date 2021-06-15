# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
#### CUANTAS MAQUINAS VIRTUALES QUIERES CREAR?
VM_NUMBER=6
  (1..VM_NUMBER).each do |i|
    config.vm.define "vm_lab_#{i}" do |node|
        node.vm.box = "centos/7"
        node.vm.hostname = "vm#{i}"
        node.vm.network :private_network, ip: "10.10.10.1#{i}"
          node.vm.provider "virtualbox" do |vb|
             vb.cpus = 1
             vb.memory = "256"
          end
    end      
  end
end
