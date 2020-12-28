# -*- mode: ruby -*-

Vagrant.configure("2") do |config|
  config.vm.box = "debian/contrib-buster64"

  config.vm.define "node1" do |node|
    node.vm.hostname = "node1"
    node.vm.network "private_network", ip: "10.0.0.2", virtualbox__intnet: "lan"
    node.vm.provision :salt do |salt|
      salt.install_master = true
      salt.master_config = 'master-config'
      salt.minion_config = 'minions-config'

      # DO NOT USE THESE KEYS IN PRODUCTION
      salt.minion_key = "key/node1.pem"
      salt.minion_pub = "key/node1.pub"
      salt.seed_master = {node1: salt.minion_pub,
                          node2: "key/node2.pub"}
      salt.verbose = true
    end
  end

  config.vm.define "node2" do |node|
    node.vm.hostname = "node2"
    node.vm.network "private_network", ip: "10.0.0.3", virtualbox__intnet: "lan"
    node.vm.provision :salt do |salt|
      salt.install_master = false
      salt.minion_config = 'minions-config'

      # DO NOT USE THESE KEYS IN PRODUCTION      
      salt.minion_key = "key/node2.pem"
      salt.minion_pub = "key/node2.pub"
      salt.verbose = true
    end
  end
end
