# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "bento/ubuntu-18.04"
  config.vm.hostname = "jekyll"
  config.vm.define "github-pages" do |base|
  end

  # Map localhost:4000 to port 4000 inside the VM
  config.vm.network "forwarded_port", guest: 4000, host: 4000
  config.ssh.forward_agent = true

  # VirtualBox-specific configuration
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", 512]
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = '.ansible/playbook.yml'
    ansible.limit    = 'all'
    # ansible.inventory_path = 'inventory_dev.py'
    ansible.extra_vars = {
        ansible_connection: 'local'
    }
end


end

