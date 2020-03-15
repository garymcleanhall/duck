# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "envimation/ubuntu-xenial-docker"
  config.disksize.size = '20GB'

  # NOTE: This will enable public access to the opened port
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  
  config.vm.synced_folder ".", "/duck"

  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "8192"
  end
  
  config.vm.provision "docker" do |d|
    d.build_image "/duck", args: "-t spectresystems/duck"
    d.run "spectresystems/duck", args: "-it -v /duck/data:/data -p 8080:15825", cmd: "start --config /data/duck.json"

  end  
end
