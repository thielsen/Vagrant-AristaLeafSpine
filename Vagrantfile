# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
box_image = "vEOS-lab-4.20.1F"

Vagrant.configure("2") do |config|
  config.vm.define "spine01" do |spine01|
    spine01.vm.box = box_image
    spine01.vm.hostname = 'spine01'
    spine01.vm.network 'private_network',
       virtualbox__intnet: 's01l01',
       ip: '169.254.1.11', auto_config: false
    spine01.vm.network 'private_network',
       virtualbox__intnet: 's01l02',
       ip: '169.254.1.11', auto_config: false
    spine01.vm.network 'private_network',
       virtualbox__intnet: 's01l03',
       ip: '169.254.1.11', auto_config: false
    spine01.vm.network 'private_network',
       virtualbox__intnet: 's01l04',
       ip: '169.254.1.11', auto_config: false
    spine01.vm.network 'private_network',
       virtualbox__intnet: 's01s02',
       ip: '169.254.1.11', auto_config: false
    spine01.vm.provision 'shell', inline: <<-SHELL
      sleep 30
      FastCli -p 15 -c "configure
      hostname spine01
      interface Management1
         ip address 192.168.56.101/24 secondary"
      SHELL
  end
  config.vm.define "spine02" do |spine02|
    spine02.vm.box = box_image
    spine02.vm.hostname = 'spine02'
    spine02.vm.network 'private_network',
       virtualbox__intnet: 's02l01',
       ip: '169.254.1.11', auto_config: false
    spine02.vm.network 'private_network',
       virtualbox__intnet: 's02l02',
       ip: '169.254.1.11', auto_config: false
    spine02.vm.network 'private_network',
       virtualbox__intnet: 's02l03',
       ip: '169.254.1.11', auto_config: false
    spine02.vm.network 'private_network',
       virtualbox__intnet: 's02l04',
       ip: '169.254.1.11', auto_config: false
    spine02.vm.network 'private_network',
       virtualbox__intnet: 's01s02',
       ip: '169.254.1.11', auto_config: false
    spine02.vm.provision 'shell', inline: <<-SHELL
       sleep 30
       FastCli -p 15 -c "configure
       hostname spine02
       interface Management1
          ip address 192.168.56.102/24 secondary"
       SHELL
  end
  config.vm.define "leaf01" do |leaf01|
    leaf01.vm.box = box_image
    leaf01.vm.hostname = "leaf01"
    leaf01.vm.network 'private_network',
       virtualbox__intnet: 's01l01',
       ip: '169.254.1.11', auto_config: false
    leaf01.vm.network 'private_network',
       virtualbox__intnet: 's02l01',
       ip: '169.254.1.11', auto_config: false
    leaf01.vm.network 'private_network',
       virtualbox__intnet: 'l01l02',
       ip: '169.254.1.11', auto_config: false
    leaf01.vm.provision 'shell', inline: <<-SHELL
       sleep 30
       FastCli -p 15 -c "configure
       hostname leaf01
       interface Management1
            ip address 192.168.56.103/24 secondary"
       SHELL
  end
  config.vm.define "leaf02" do |leaf02|
    leaf02.vm.box = box_image
    leaf02.vm.hostname = "leaf02"
    leaf02.vm.network 'private_network',
       virtualbox__intnet: 's01l02',
       ip: '169.254.1.11', auto_config: false
    leaf02.vm.network 'private_network',
       virtualbox__intnet: 's02l02',
       ip: '169.254.1.11', auto_config: false
    leaf02.vm.network 'private_network',
       virtualbox__intnet: 'l01l02',
       ip: '169.254.1.11', auto_config: false
    leaf02.vm.provision 'shell', inline: <<-SHELL
       sleep 30
       FastCli -p 15 -c "configure
       hostname leaf02
       interface Management1
           ip address 192.168.56.104/24 secondary"
       SHELL
  end
  config.vm.define "leaf03" do |leaf03|
    leaf03.vm.box = box_image
    leaf03.vm.hostname = "leaf03"
    leaf03.vm.network 'private_network',
       virtualbox__intnet: 's01l03',
       ip: '169.254.1.11', auto_config: false
    leaf03.vm.network 'private_network',
       virtualbox__intnet: 's02l03',
       ip: '169.254.1.11', auto_config: false
    leaf03.vm.network 'private_network',
       virtualbox__intnet: 'l03l04',
       ip: '169.254.1.11', auto_config: false
    leaf03.vm.provision 'shell', inline: <<-SHELL
       sleep 30
       FastCli -p 15 -c "configure
       hostname leaf03
       interface Management1
           ip address 192.168.56.105/24 secondary"
       SHELL
  end
  config.vm.define "leaf04" do |leaf04|
    leaf04.vm.box = box_image
    leaf04.vm.hostname = "leaf04"
    leaf04.vm.network 'private_network',
       virtualbox__intnet: 's01l04',
       ip: '169.254.1.11', auto_config: false
    leaf04.vm.network 'private_network',
       virtualbox__intnet: 's02l04',
       ip: '169.254.1.11', auto_config: false
    leaf04.vm.network 'private_network',
       virtualbox__intnet: 'l03l04',
       ip: '169.254.1.11', auto_config: false
    leaf04.vm.provision 'shell', inline: <<-SHELL
      sleep 30
      FastCli -p 15 -c "configure
        hostname leaf04
        interface Management1
           ip address 192.168.56.106/24 secondary"
        SHELL
  end
end


  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
