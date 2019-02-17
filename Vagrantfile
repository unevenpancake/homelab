# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box = "eightbitdino/homelab"
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.network "private_network", ip: "192.168.126.101"

  config.vm.provider "vmware_desktop" do |vmware|
    vmware.vmx["vhv.enable"] = "TRUE"
  end

  config.vm.provider "libvirt" do |libvirt|
    libvirt.nested = true
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbooks/zerotier.yml"
  end
end
