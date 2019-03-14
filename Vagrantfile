# -*- mode: ruby -*-
# vi: set ft=ruby :
unless Vagrant.has_plugin?("vagrant-docker-compose")
  system("vagrant plugin install vagrant-docker-compose")
  puts "Dependencies installed, please try the command again."
  exit
end 

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/bionic64"
  config.vm.provision :docker
  config.vm.provision :docker_compose
  config.vm.provision "shell", inline: "apt-get update && apt-get install -y python-minimal"
  config.vm.network "forwarded_port", guest: 8080, host: 8080


  config.vm.provision "ansible" do |ansible|
    # ansible.verbose = "v"
    ansible.playbook = "playbook.yml"
  end



end
