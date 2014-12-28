# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "precise32"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"
  config.vm.hostname = "atlas"

  config.vm.network :forwarded_port, guest: 8080, host: 8080
  config.vm.network :forwarded_port, guest: 8090, host: 8090
  config.vm.network :forwarded_port, guest: 7990, host: 7990
  config.vm.network :forwarded_port, guest: 8085, host: 8085

  config.vm.provider :virtualbox do |vb|
  # Use VBoxManage to customize the VM. For example to change memory:
    vb.customize ["modifyvm", :id, 
      "--name", "atlas",
      "--memory", "4096",
      # Enable DNS behind NAT
      "--natdnshostresolver1", "on"]
  end

  config.vm.provision :puppet, :module_path => "modules" do |puppet|
    puppet.manifests_path = "manifests"
    puppet.manifest_file  = "default.pp"
  end

end
