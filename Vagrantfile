# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"

  # Airflow webserver
  (1..1).each do |i|
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end

    config.vm.define "airflow-web0#{i}" do |server|
      server.vm.hostname = "airflow-web0#{i}"
      server.vm.network "private_network", ip: "10.0.1.8#{i}"
    end
  end

  # Airflow worker
  # (1..1).each do |i|
  #   config.vm.provider "virtualbox" do |vb|
  #     vb.memory = 2048
  #     vb.cpus = 2
  #   end
  #
  #   config.vm.define "airflow-worker0#{i}" do |server|
  #     server.vm.hostname = "airflow-worker0#{i}"
  #     server.vm.network "private_network", ip: "10.0.1.9#{i}"
  #   end
  # end

  # Provision
  config.vm.provision "shell", path: "provision.sh"
  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/authorized_keys"

end
