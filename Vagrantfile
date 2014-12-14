# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
  # Box
  config.vm.box = 'ubuntu/trusty64'
  config.vm.provider 'virtualbox' do |v|
    v.name = 'openl10n'
    v.memory = 1024
    v.cpus = 2
  end

  # Project
  nfs_setting = RUBY_PLATFORM =~ /darwin/ || RUBY_PLATFORM =~ /linux/
  config.vm.synced_folder './openl10n', '/var/www/openl10n.dev/current', :nfs => nfs_setting

  # Network
  config.vm.hostname = 'openl10n.dev'
  config.vm.network :private_network, ip: '10.0.0.42'
  config.ssh.forward_agent = true

  # Provisioning (Ansible - https://docs.vagrantup.com/v2/provisioning/ansible.html)
  config.vm.provision 'ansible' do |ansible|
    ansible.sudo = true
    ansible.limit = 'vagrant'
    ansible.playbook = 'provisioning/playbook.yml'
    ansible.inventory_path = 'provisioning/hosts/vagrant'
    ansible.verbose = 'v'
  end
end
