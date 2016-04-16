# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # https://docs.vagrantup.com.
  config.vm.box = "ubuntu/trusty64"

  config.vm.network :forwarded_port, guest: 22, host: 3234

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 4 * 1024;
    vb.cpus = 4
  end

  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install emacs24-nox
    wget -q -O- https://s3.amazonaws.com/download.fpcomplete.com/ubuntu/fpco.key | sudo apt-key add -
    echo 'deb http://download.fpcomplete.com/ubuntu/trusty stable main' | sudo tee /etc/apt/sources.list.d/fpco.list
    sudo apt-get update && sudo apt-get install stack -y
  SHELL
end

