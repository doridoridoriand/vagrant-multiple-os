# -*- mode: ruby -*-
# vi: set ft=ruby :

configure = YAML.load_file(File.join(__dir__, 'configure.yml'))

memory_default = configure.map {|r| r['memory']}.compact.first
cpu_default    = configure.map {|r| r['cpus']}.compact.first
vms            = configure.map {|r| r['vms']}.compact.flatten

vms.map {|vm| vm.store('memory', memory_default) unless vm['memory']}
vms.map {|vm| vm.store('cpus',   cpu_default)    unless vm['cpu']}

Vagrant.configure(2) do |config|
  vms.each_with_index do |vm, i|
    config.vm.define vm['name'] do |o|
      o.vm.box = vm['os']
      o.vm.hostname = vm['name']
      o.vm.network 'private_network', ip: "192.168.56.#{100 + i}"
      o.vm.provider 'virtualbox' do |vb|
        vb.memory = vm['memory']
        vb.cpus   = vm['cpus']
      end
    end
  end
end
