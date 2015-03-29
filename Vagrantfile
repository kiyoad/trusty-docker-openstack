# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.define :controller do |conf|
    conf.vm.hostname = "controller.local"
    conf.vm.network :private_network, ip: "10.0.0.11"
    conf.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", "4096" ]
    end
  end

  config.vm.define :network do |conf|
    conf.vm.hostname = "network.local"
    conf.vm.network :private_network, ip: "10.0.0.21"
    conf.vm.network :private_network, ip: "10.0.1.21"
    conf.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", "512" ]
    end
  end

  config.vm.define :compute1 do |conf|
    conf.vm.hostname = "compute1.local"
    conf.vm.network :private_network, ip: "10.0.0.31"
    conf.vm.network :private_network, ip: "10.0.1.31"
    conf.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", "2048" ]
    end
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/site.yml"
  end

end
