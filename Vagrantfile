Vagrant.configure("2") do |config|
    config.vm.box = "precise64"
    config.vm.box_url = "http://files.vagrantup.com/precise64.box"
    config.vm.hostname = "OpenMRSDev"
    config.vm.synced_folder "shared", "/home/vagrant/Shared"
    config.vm.synced_folder "projects", "/home/vagrant/Projects"
    config.vm.network "public_network"
    config.vm.network :private_network, ip: "192.168.127.200"
    config.vm.network "forwarded_port", guest: 8080, host: 8080, auto_correct: true
    config.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--memory", 2048]
    end
    config.vm.provision :ansible do |ansible|
        ansible.limit = "all"
        ansible.playbook = "ansible/playbook.yml"
        ansible.inventory_path = "ansible/ansible_hosts"
        # Use inventory_file if using Vagrant 1.2.x
        # ansible.inventory_file = "ansible/ansible_hosts"
        ansible.verbose = true
        # All hosts line required for newest vagrant version 1.5.x 
        ansible.hosts = "all"
    end
    config.ssh.forward_agent = true
    config.ssh.forward_x11 = true
end
