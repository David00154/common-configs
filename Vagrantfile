# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<-'SCRIPT'
echo "i am $USER"
SCRIPT

Vagrant.configure("2") do |config|


  # Configuration for master vm
  config.vm.define "master" do |master|
    master.vm.box  = "hashicorp/bionic64"
    # master.vm.hostname "master"
    master.vm.network "public_network"
    master.vm.provider "hyperv"
    master.vm.hostname  = "master"
    master.vm.synced_folder ".", "/vagrant", disabled: true
    master.vm.provision "shell", inline: $script
    master.vm.network "public_network", bridge: "Default Switch"
    master.vm.provider "hyperv" do |hv|
      hv.memory = 1048
      hv.cpus = 1
      hv.linked_clone = true
      hv.vmname = "master"
    end 
  end

  # Configuration for node1 vm
  config.vm.define "node1" do |node1|
    node1.vm.box  = "hashicorp/bionic64"
    # node1.vm.hostname "node1"
    node1.vm.network "public_network"
    node1.vm.provider "hyperv"
    node1.vm.hostname  = "node1"
    node1.vm.synced_folder ".", "/vagrant", disabled: true
    node1.vm.provision "shell", inline: $script
    node1.vm.network "public_network", bridge: "Default Switch"
    node1.vm.provider "hyperv" do |hv|
      hv.memory = 1048
      hv.cpus = 1
      hv.linked_clone = true
      hv.vmname = "node1"
    end 
  end
end

# Network Settings
  # config.vm.network "forwarded_port", guest: 80, host: 8080
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  # config.vm.network "private_network", bridge: "BRIDGE"
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Folder Settings
  # config.vm.synced_folder ".", "/var/www/html", :nfs => { :mount_options => ["dmode=777", "fmode=666"] }
  
  # config.vm.provision "shell", path: "bootstrap.sh"

# VAGRANT_DISABLE_SMBMFSYMLINKS=1
# config.vm.synced_folder '/host/path', '/guest/path', type: "smb", mount_options: ['mfsymlink']