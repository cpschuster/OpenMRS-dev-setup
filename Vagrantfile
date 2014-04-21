# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "OpenMRS-dev-setup-clone"

  # Contains working snapshot of code as of 2014-04-19
  #If you pre-downloaded file to current working directory
  #config.vm.box_url = "file://#{File.dirname(__FILE__)}/OpenMRS-dev-setup-base.box"
  config.vm.box_url = "https://googledrive.com/host/0Bw9lrNlwIuLzZDEzZ0JUOUhuQmM/OpenMRS-dev-setup-base.box"
  config.vm.hostname = "OpenMRSDev"
  config.vm.synced_folder "shared", "/home/vagrant/Shared"
  config.vm.synced_folder "projects", "/home/vagrant/Projects"
  config.vm.network "public_network"
  config.vm.network :private_network, type: "dhcp"
  config.vm.network "forwarded_port", guest: 8080, host: 8080, auto_correct: true
  config.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", 2048]
  end
  config.ssh.forward_agent = true
  config.ssh.forward_x11 = true

  move_source_code_to_synced_folder = <<-EOS
    [ -d /home/vagrant/Projects/OpenMRS ] || mv /home/vagrant/OpenMRS /home/vagrant/Projects 
EOS

  config.vm.provision :shell, :inline => move_source_code_to_synced_folder

end
