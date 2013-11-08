# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.hostname = "evergreen"
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", 4096]
  end

  config.vm.network :private_network, ip: "10.11.12.16"
  config.vm.network :forwarded_port, guest: 80, host: 3001
  config.vm.network :forwarded_port, guest: 443, host: 4443 
  config.vm.network :forwarded_port, guest: 5432, host: 5432

  config.vm.synced_folder '.', '/vagrant', disabled: true

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "vagrant.yml"
    ansible.inventory_path = "vagrant"
  end
end
