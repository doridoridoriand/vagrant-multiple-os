# -*- mode: ruby -*-
# vi: set ft=ruby :

SIZE_OF_MEMORY = 1024
NUMBER_OF_CPUS = 2

VMS = [{os: 'bento/centos-6.8', memory: SIZE_OF_MEMORY, cpus: NUMBER_OF_CPUS},
       {os: 'bento/centos-7.3', memory: SIZE_OF_MEMORY, cpus: NUMBER_OF_CPUS},
       {os: 'ubuntu/xenial64',  memory: SIZE_OF_MEMORY, cpus: NUMBER_OF_CPUS},
       {os: 'ubuntu/trusty64',  memory: SIZE_OF_MEMORY, cpus: NUMBER_OF_CPUS}]
Vagrant.configure(2) do |config|
  VMS.each_with_index do |vm, i|
    config.vm.define vm[:os].split('/').last do |o|
      o.vm.box    = vm[:os]
      o.vm.network 'private_network', ip: "192.168.33.#{100 + i}"
      o.vm.provider 'virtualbox' do |vb|
        vb.memory = vm[:memory]
        vb.cpus   = vm[:cpus]
      end
    end
  end
end
