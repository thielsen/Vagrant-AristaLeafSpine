# -*- mode: ruby -*-
# vi: set ft=ruby :

box_image = "vEOS-lab-4.20.1F"

Vagrant.configure("2") do |config|
  config.vm.define "spine01" do |spine01|
    spine01.vm.box = box_image
    spine01.vm.hostname = 'spine01'
    spine01.vm.network "private_network", ip: "192.168.56.101"
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
      interface Ethernet1
         no switchport
         ip address 192.168.56.101/24"
      SHELL
  end

  config.vm.define "spine02" do |spine02|
    spine02.vm.box = box_image
    spine02.vm.hostname = 'spine02'
    spine02.vm.network "private_network", ip: "192.168.56.102"
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
       interface Ethernet1
          no switchport
          ip address 192.168.56.102/24"
       SHELL
  end

  config.vm.define "leaf01" do |leaf01|
    leaf01.vm.box = box_image
    leaf01.vm.hostname = "leaf01"
    leaf01.vm.network "private_network", ip: "192.168.56.103"
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
       interface Ethernet1
          no switchport
          ip address 192.168.56.103/24"
       SHELL
  end

  config.vm.define "leaf02" do |leaf02|
    leaf02.vm.box = box_image
    leaf02.vm.hostname = "leaf02"
    leaf02.vm.network "private_network", ip: "192.168.56.104"
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
       interface Ethernet1
           no switchport
           ip address 192.168.56.104/24"
       SHELL
  end

  config.vm.define "leaf03" do |leaf03|
    leaf03.vm.box = box_image
    leaf03.vm.hostname = "leaf03"
    leaf03.vm.network "private_network", ip: "192.168.56.105"
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
       interface Ethernet1
           no switchport
           ip address 192.168.56.105/24"
       SHELL
  end

  config.vm.define "leaf04" do |leaf04|
    leaf04.vm.box = box_image
    leaf04.vm.hostname = "leaf04"
    leaf04.vm.network "private_network", ip: "192.168.56.106"
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
        interface Ethernet1
           no switchport
           ip address 192.168.56.106/24"
        SHELL
  end
end
