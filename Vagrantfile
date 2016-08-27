# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    # Update the OS
    apt-get update

    # Install things we need
    apt-get install build-essential git -y

    # Create afl directory and mount it as a 1GB RAMDisk
    mkdir ./afl
    mount -o size=1G -t ramfs none ./afl
    cd ./afl

    # Git clone and make AFL
    git init
    git remote add origin https://github.com/mcarpenter/afl
    git fetch --depth=1 origin
    git checkout -b master --track origin/master
    make install

    # AFL tells you to do this, so do it
    echo core > /proc/sys/kernel/core_pattern
  SHELL
end
