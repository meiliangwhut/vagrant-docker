# -*- mode: ruby -*-
# vi: set ft=ruby :

$bootstrap=<<SCRIPT
apt-get update
curl -sSL https://get.docker.com/ | sudo sh
gpasswd -a vagrant docker
service docker restart
curl -sSL https://get.daocloud.io/daotools/set_mirror.sh | sh -s http://ab1d5499.m.daocloud.io
service docker restart
apt-get install -qy build-essential bsdtar curl
apt-get install -qy git
cp /vagrant/docker-compose-Linux-x86_64 /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
apt-get install -qy cscope
wget http://nginx.org/download/nginx-1.9.9.tar.gz
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = false
  config.vm.hostname = "docker"
  config.vm.network :private_network, ip: "192.168.33.10"
  config.vm.provision :shell, inline: $bootstrap 
end
