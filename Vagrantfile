# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.define "mamebox" do |mamebox|
    mamebox.vm.box = "ubuntu/trusty64"

    mamebox.vm.hostname = "local.mamebox.com"

    mamebox.vm.network "private_network", ip: "192.168.88.10"

    mamebox.vm.synced_folder "../roms", "/var/roms", type: "nfs"

    mamebox.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.name = "mamebox"
    end

    mamebox.vm.provision "ansible" do |ansible|
      ansible.groups = {
        "mamebox" => [ "mamebox" ],
      }

      ansible.playbook = "ansible/site.yml"

      ansible.extra_vars = { ansible_ssh_user: "vagrant" }
      ansible.sudo = true;
    end
  end
end
