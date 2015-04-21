# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "base"

  config.vm.network :private_network, type: 'dhcp'
  config.vm.network "forwarded_port", guest: 3000, host: 3000

  config.vm.synced_folder '~/go', '/home/vagrant/go', nfs: true

  config.vm.box = "hashicorp/precise32"
  config.vm.provision :shell, path: "bootstrap.sh"
  config.vm.provision "chef_solo" do |chef|
    chef.add_recipe "golang"
    chef.add_recipe "redisio"
    chef.add_recipe "rabbitmq"
  end
end
