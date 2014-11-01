# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "ufw" do |ufw|
    ufw.vm.hostname = "ufw"
    ufw.vm.box = "hashicorp/precise64"
    ufw.vm.network "private_network", ip: "192.168.0.2"

    ufw.vm.provision "ansible" do |ansible|
      ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
      ansible.verbose    = "v"
      ansible.playbook   = "ufw-example.yml"
    end
  end
end
