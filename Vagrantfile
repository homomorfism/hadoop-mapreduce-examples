# -*- mode: ruby -*-
# vi: set ft=ruby :
BOX_PATH = 'hadoop_image.box'

Vagrant.configure("2") do |config|

 config.vm.define "server-1" do |subconfig|
   subconfig.vm.box = "server-1" #BOX_IMAGE
   subconfig.vm.box_url = BOX_PATH
   subconfig.vm.hostname = "server-1"
   subconfig.vm.network :private_network, ip: "10.0.0.11"
   subconfig.vm.network "forwarded_port", guest: 8088, host: 8088
   subconfig.vm.provider "virtualbox" do |v|
    v.memory = 512
   end
 end

 config.vm.define "server-2" do |subconfig|
   subconfig.vm.box = "server-2" #BOX_IMAGE
   subconfig.vm.box_url = BOX_PATH
   subconfig.vm.hostname = "server-2"
   subconfig.vm.network :private_network, ip: "10.0.0.12"
   subconfig.vm.provider "virtualbox" do |v|
    v.memory = 512
   end
 end

 config.vm.define "server-3" do |subconfig|
   subconfig.vm.box = "server-3" #BOX_IMAGE
   subconfig.vm.box_url = BOX_PATH
   subconfig.vm.hostname = "server-3"
   subconfig.vm.network :private_network, ip: "10.0.0.13"
   subconfig.vm.provider "virtualbox" do |v|
    v.memory = 512
   end
 end

end
