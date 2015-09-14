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

  config.vm.define "agent_1" do |agent_1|
    agent_1.vm.box_url = "https://vagrantcloud.com/ubuntu/trusty64"
    agent_1.vm.box = "ubuntu/trusty64"

    agent_1.vm.hostname = "go-agent-1"
    agent_1.vm.network :private_network, type: "dhcp"

    agent_1.vm.provision "ansible" do |ansible|
      ansible.playbook = "agent.yml"
    end

    if Vagrant.has_plugin?("vagrant-cachier")
      agent_1.cache.scope = :machine
    end

    agent_1.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end
  end

  config.vm.define "agent_2" do |agent_2|
    agent_2.vm.box_url = "https://vagrantcloud.com/ubuntu/trusty64"
    agent_2.vm.box = "ubuntu/trusty64"

    agent_2.vm.hostname = "go-agent-2"
    agent_2.vm.network :private_network, type: "dhcp"

    agent_2.vm.provision "ansible" do |ansible|
      ansible.playbook = "agent.yml"
    end

    if Vagrant.has_plugin?("vagrant-cachier")
      agent_2.cache.scope = :machine
    end

    agent_2.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end
  end
end
