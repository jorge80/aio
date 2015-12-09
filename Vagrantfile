# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

# set to false, if you do NOT want to check the correct VirtualBox Guest Additions version when booting this box
  Vagrant.configure("2") do |config|
# Every Vagrant virtual environment requires a box to build off of.
# Disable automatic box update checking. If you disable this, then
# boxes will only be checked for updates when the user runs
# `vagrant box outdated`. This is not recommended.
# config.vm.box_check_update = false
  config.vm.box = "ubuntu/trusty32"
# The url from where the 'config.vm.box' box will be fetched if it
# doesn't already exist on the user's system. 
# config.vm.box_url = "https://atlas.hashicorp.com/ubuntu/boxes/trusty32/versions/20151203.2.0/providers/virtualbox.box"
  
# Provider-specific configuration so you can fine-tune various
# backing providers for Vagrant. These expose provider-specific options.
# Example for VirtualBox:
#
# config.vm.provider "virtualbox" do |vb|
#   # Display the VirtualBox GUI when booting the machine
#   vb.gui = true
#
#   # Customize the amount of memory on the VM:
#   vb.memory = "2500"
# end
#
# View the documentation for the provider you are using for more
# information on available options.  
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id,"--cpus", "1", "--memory", "3200"]
    vb.customize ["modifyvm", :id, "--vram", "16"]
    vb.name = "trusty32"
  end
  
# Shared folders
# Share an additional folder to the guest VM. The first argument is
# the path on the host to the actual folder. The second argument is
# the path on the guest to mount the folder. And the optional third
# argument is a set of non-required options.
  config.vm.synced_folder ".", "/app"
  
  config.vm.provision :shell, :inline => "apt-get update --fix-missing"
  config.vm.provision :shell,
  :keep_color => true
# Create a forwarded port mapping which allows access to a specific port
# within the machine from a port on the host machine. In the example below,
# accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network :forwarded_port, guest: 5601, host: 5601, auto_correct: true 
  config.vm.network :forwarded_port, guest: 9200, host: 9200, auto_correct: true
  config.vm.network :forwarded_port, guest: 9300, host: 9300, auto_correct: true
  config.vm.network :forwarded_port, guest: 8787, host: 8787, auto_correct: true
  config.vm.network :forwarded_port, guest: 1337, host: 1337, auto_correct: true
  config.vm.network :forwarded_port, guest: 4040, host: 4040, auto_correct: true
  config.vm.network :forwarded_port, guest: 9000, host: 9000, auto_correct: true
  config.vm.network :forwarded_port, guest: 8080, host: 8080, auto_correct: true
# Create a private network, which allows host-only access to the machine
# using a specific IP.
# config.vm.network "private_network", ip: "192.168.33.10"

# Create a public network, which generally matched to bridged network.
# Bridged networks make the machine appear as another physical device on
# your network.
# config.vm.network "public_network"
  
# So graphical programs may be used from the VM
  config.ssh.forward_x11 = true 
  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
end
