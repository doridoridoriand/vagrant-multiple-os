# -*- mode: ruby -*-
# vi: set ft=ruby :

SIZE_OF_MEMORY = 1024
NUMBER_OF_CPUS = 2

VMS = ['bento/centos-6.8', 'bento/centos-7.3', 'ubuntu/xenial64', 'ubuntu/trusty64']
DEFINES = VMS.map {|os| os.split('/').last}

Vagrant.configure(2) do |config|
  config.vm.provider 'virtualbox' do |vb|
    vb.memory = SIZE_OF_MEMORY
    vb.cpus   = NUMBER_OF_CPUS
  end
  VMS.each_with_index do |os, i|
    config.vm.define DEFINES[i] do |o|
      o.vm.box    = os
      o.vm.network 'private_network', ip: "192.168.33.#{100 + i}"
    end
  end
end
