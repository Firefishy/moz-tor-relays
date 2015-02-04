# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "chef/centos-7.0"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.define 'tor-vagrant' do |machine|
    machine.vm.hostname = 'tor-vagrant'
    machine.vm.network "private_network", ip: "192.168.177.122"
  end

  config.vm.synced_folder '.', '/vagrant', disabled: true

  config.vm.provision "ansible" do |ansible|
    ansible.groups = { "tor-relays" => ["tor-vagrant"] }
    ansible.playbook = "tor.yml"
  end
end
