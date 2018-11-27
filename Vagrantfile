# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "eightbitdino/homelab"
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.network "private_network", ip: "192.168.125.101"

  config.vm.provider "vmware_desktop" do |vmware|
    vmware.vmx["vhv.enable"] = "TRUE"
  end

  config.vm.provider "libvirt" do |libvirt|
    libvirt.nested = true
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbooks/libvirt.yml"
  end
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbooks/docker.yml"
  end

  config.trigger.after :up do |trigger|
    trigger.info = "Inject newest ssh config information to sshconfig file"
    trigger.run = {inline: "echo $HOME"}
  end
end
