Vagrant.configure("2") do |config|
    config.vm.box = "precise64"
    config.vm.box_url = "http://files.vagrantup.com/precise64.box"
    config.vm.hostname = "DevMachine1"
    config.vm.synced_folder "shared", "/home/vagrant/Shared"
    config.vm.network "public_network"
    config.vm.network :private_network, ip: "192.168.127.200"
    config.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--memory", 1024]
    end
    config.vm.provision :ansible do |ansible|
        ansible.playbook = "ansible/playbook.yml"
        ansible.inventory_path = "ansible/ansible_hosts"
        ansible.verbose = true
    end
    config.ssh.forward_agent = true
    config.ssh.forward_x11 = true
end
