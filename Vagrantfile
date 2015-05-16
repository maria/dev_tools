# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty64"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network :private_network, ip: "192.168.10.3"
  config.vm.host_name = "minideb.local"

  config.vm.synced_folder ".", "/home/vagrant/dev_tools"
  config.vm.synced_folder "../SkillHub", "/home/vagrant/SkillHub", create: true

  config.vm.provision :ansible do |ansible|
    ansible.playbook  = "config/provision.yml"
    ansible.inventory_path = "config/hosts.ini"
    ansible.verbose = "v"
  end

  config.vm.provider :virtualbox do |vb|
    vb.name = "minideb"
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end
end
