# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

# set to false, if you do NOT want to check the correct VirtualBox Guest Additions version when booting this box
  Vagrant.configure("2") do |config|
    config.vbguest.auto_update = false
  end
# Every Vagrant virtual environment requires a box to build off of. 
config.vm.box = "ubuntu/trusty32"
# The url from where the 'config.vm.box' box will be fetched if it
# doesn't already exist on the user's system. 
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-i386-vagrant-disk1.box"
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id,"--cpus", "1", "--memory", "3200"]
    vb.customize ["modifyvm", :id, "--vram", "16"]
    vb.name = "trusty32"
  end
  
# Shared folders
  config.vm.synced_folder ".", "/app"
  
  config.vm.provision :shell, :inline => "apt-get update --fix-missing"
  config.vm.provision :shell,
  :keep_color => true
  
  config.vm.network :forwarded_port, guest: 5601, host: 5601, auto_correct: true 
  config.vm.network :forwarded_port, guest: 9200, host: 9200, auto_correct: true
  config.vm.network :forwarded_port, guest: 9300, host: 9300, auto_correct: true
  config.vm.network :forwarded_port, guest: 8787, host: 8787, auto_correct: true
  config.vm.network :forwarded_port, guest: 1337, host: 1337, auto_correct: true
  config.vm.network :forwarded_port, guest: 4040, host: 4040, auto_correct: true
  config.vm.network :forwarded_port, guest: 9000, host: 9000, auto_correct: true
  config.vm.network :forwarded_port, guest: 8080, host: 8080, auto_correct: true
  
# So graphical programs may be used from the VM
  config.ssh.forward_x11 = true 
  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"

  end
end
