# -*- mode: ruby -*-
# vi: set ft=ruby :

$docker_swarm_init = <<INIT
echo "============== Initializing swarm mode ====================="
docker swarm init --advertise-addr 192.168.1.100 --listen-addr 192.168.1.100:2377
docker swarm join-token --quiet worker > /vagrant/worker_token
INIT

$docker_swarm_join_worker = <<JOIN
echo "============== Joining swarm cluster as worker ====================="
docker swarm join --token $(cat /vagrant/worker_token) 192.168.1.100:2377
JOIN


Vagrant.configure("2") do |config|
	config.vm.provision "docker"
  config.vm.provision "docker_compose"


  config.ssh.insert_key = false

  config.vm.define "node1" do |node1|
      config.vm.box = "debian/bullseye64"
      node1.vm.hostname = "node1"
      node1.vm.network "public_network", ip: "192.168.1.100"
      node1.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
      node1.vm.synced_folder "./docker", "/vagrant"
      node1.vm.provision :shell, inline: $docker_swarm_init
    end

    config.vm.define "node2" do |node2|
      config.vm.box = "debian/bullseye64"
      node2.vm.hostname = 'node2'
      node2.vm.network :public_network, ip: "192.168.1.101"
      node2.vm.synced_folder "./docker", "/vagrant"
      node2.vm.provision :shell, inline: $docker_swarm_join_worker
    end

  end

