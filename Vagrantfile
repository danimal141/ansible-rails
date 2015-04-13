# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define :develop do |node|
    node.vm.box = 'ubuntu/trusty64'
    node.vm.network 'private_network', ip: '192.168.33.10'
    node.vm.hostname = "dev.danimal141.com"
    node.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
    end

    node.vm.provision :ansible do |ansible|
      ansible.playbook = 'site.yml'
      ansible.inventory_path = 'hosts_develop'
      ansible.verbose = 'vvvv'
      ansible.ask_sudo_pass = true
      #ansible.tags = 'nginx' # To run individual roles
    end
  end
end
