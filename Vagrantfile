# -*- mode: ruby -*-
# vi: set ft=ruby :

# General project settings
#################################

  # IP Address for the host only network, change it to anything you like
  # but please keep it within the IPv4 private network range
  ip_address = "172.16.46.5"

  # The project name is base for directories, hostname and alike
  project_name = "moodle"



Vagrant.configure(2) do |config|
	#config.vm.hostname = 'moodle.local'
	config.vm.box = "ubuntu/trusty64"
	#config.vm.network "private_network", ip: "172.16.46.5"
	config.vm.synced_folder "./moodle/", "/var/www/moodle", create: true, owner: 'www-data', group: 'www-data'
	
	config.hostmanager.enabled = true
	config.hostmanager.manage_host = true
  	config.vm.define project_name do |node|
    	node.vm.hostname = project_name + ".local"
    	node.vm.network :private_network, ip: ip_address
    	node.hostmanager.aliases = [ "www." + project_name + ".local" ]
	end
	config.vm.provider "virtualbox" do |vb|
		vb.name = "moodle"
		vb.memory = 2048 
		vb.cpus = 2
	end
	config.vm.provision :shell, path: "provision.sh"
end
