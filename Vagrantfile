# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ie8_win7"
  config.vm.box_url = "http://aka.ms/vagrant-win7-ie8"
  config.vm.guest = :windows
  config.vm.communicator = "winrm"
  config.winrm.username = "IEUser"
  config.winrm.password = "Passw0rd!"

  config.vm.provider "virtualbox" do |v|
    v.gui = true
  end

  config.vm.network "private_network", ip: "10.42.0.201"

end
