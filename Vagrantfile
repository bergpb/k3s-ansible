# -*- mode: ruby -*-
# vi: set ft=ruby :

machines = {
  "main" => {"memory" => "1024", "cpu" => "1", "ip" => "10", "image" => "ubuntu/bionic64"},
  "worker1" => {"memory" => "512", "cpu" => "1", "ip" => "20", "image" => "ubuntu/bionic64"},
  "worker2" => {"memory" => "512", "cpu" => "1", "ip" => "30", "image" => "ubuntu/bionic64"}
}

Vagrant.configure("2") do |config|

  machines.each do |name, conf|
    config.vm.define "#{name}" do |machine|
      machine.vm.box = "#{conf["image"]}"
      machine.vm.hostname = "#{name}.bergpb.dev"
      machine.vm.network "private_network", ip: "192.168.56.#{conf["ip"]}"
      machine.vm.provider "virtualbox" do |vb|
        vb.name = "#{name}"
        vb.memory = conf["memory"]
        vb.cpus = conf["cpu"]
      end
      machine.ssh.insert_key = false
      machine.ssh.private_key_path = File.expand_path("~/.vagrant.d/insecure_private_key")
    end
  end
end
