# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "server" do |server|
    server.vm.box_url = "https://vagrantcloud.com/ubuntu/trusty64"
    server.vm.box = "ubuntu/trusty64"

    server.vm.hostname = "go-server"
    server.vm.network :private_network, type: "dhcp"

    server.vm.provision "ansible" do |ansible|
      ansible.playbook = "server.yml"
    end

    if Vagrant.has_plugin?("vagrant-cachier")
      server.cache.scope = :machine
    end

    server.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end
  end

  config.vm.define "agent" do |agent|
    agent.vm.box_url = "https://vagrantcloud.com/ubuntu/trusty64"
    agent.vm.box = "ubuntu/trusty64"

    agent.vm.hostname = "go-server"
    agent.vm.network :private_network, type: "dhcp"

    agent.vm.provision "ansible" do |ansible|
      ansible.playbook = "agent.yml"
    end

    if Vagrant.has_plugin?("vagrant-cachier")
      agent.cache.scope = :machine
    end

    agent.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end
  end
end
