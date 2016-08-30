# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.require_version '>= 1.8'

Vagrant.configure(2) do |config|
    #Image from https://vagrantcloud.com/jhakonen/boxes/windows-10-n-pro-en-x86_64
    config.vm.box = "jhakonen/windows-10-n-pro-en-x86_64"
    config.vm.communicator = "winrm"
    # Admin user name and password
    config.winrm.username = "vagrant"
    config.winrm.password = "vagrant"
    config.vm.guest = :windows
    config.vm.network :forwarded_port, guest: 3389, host: 3389, id: "rdp", auto_correct: true
    config.vm.network :forwarded_port, guest: 22, host: 2222, id: "ssh", auto_correct: true
    if Vagrant.has_plugin?('vagrant-vbguest')
      config.vbguest.auto_update = false
    end

    config.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.customize ["modifyvm", :id, "--vram", "256", "--cpus", "2", "--ioapic", "on"]
      vb.gui = true
      vb.customize ["setextradata", "global", "GUI/SuppressMessages", "all" ]
    end
end
