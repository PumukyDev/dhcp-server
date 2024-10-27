# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.vm.box_check_update = false
  config.ssh.insert_key = false
  config.vm.provider :virtualbox do |vb|
    vb.memory = 256
    vb.cpus = 1
  end

  config.vm.define "server" do |s|
    s.vm.hostname = "server"
    s.vm.network "private_network", ip: "192.168.60.10"
    s.vm.network "private_network", ip: "192.168.61.15", virtualbox__intnet: "lab1"
    s.vm.network "private_network", ip: "192.168.62.15", virtualbox__intnet: "lab2"
    s.vm.network "private_network", ip: "192.168.63.15", virtualbox__intnet: "lab3"
    s.vm.network "private_network", ip: "192.168.64.15", virtualbox__intnet: "asir"
    s.vm.network "private_network", ip: "192.168.65.15", virtualbox__intnet: "aula_convivencia"
    s.vm.provider :virtualbox do |vb|
      vb.memory = 512
      vb.cpus = 1
    end
    s.vm.provision "shell", inline: <<-SHELL
      apt-get update -y
      apt-get install -y isc-dhcp-server
      cp -v /vagrant/dhcp-conf/isc-dhcp-server /etc/default/
      cp -v /vagrant/dhcp-conf/dhcpd.conf /etc/dhcp/
      systemctl restart isc-dhcp-server
    SHELL
  end

  config.vm.define "Pepe" do |pepe|
    pepe.vm.hostname = "pepe"
    pepe.vm.network "private_network", mac: "0000c05dbd90", type: "dhcp", virtualbox__intnet: "lab1"
  end

  config.vm.define "Diego" do |diego|
    diego.vm.hostname = "diego"
    diego.vm.network "private_network", mac: "0000c05dbd91", type: "dhcp", virtualbox__intnet: "lab2"
  end

  config.vm.define "Profelab" do |profelab|
    profelab.vm.hostname = "profelab"
    profelab.vm.network "private_network", mac: "0000c05dbd92", type: "dhcp", virtualbox__intnet: "lab3"
  end

  config.vm.define "Adrian" do |adrian|
    adrian.vm.hostname = "adrian"
    adrian.vm.network "private_network", mac: "0000c05dbd93", type: "dhcp", virtualbox__intnet: "asir"
  end

  config.vm.define "Jesus" do |jesus|
    jesus.vm.hostname = "jesus"
    jesus.vm.network "private_network", mac: "0000c05dbd94", type: "dhcp", virtualbox__intnet: "asir"
  end

  config.vm.define "Pablo" do |pablo|
    pablo.vm.hostname = "pablo"
    pablo.vm.network "private_network", mac: "0000c05dbd95", type: "dhcp", virtualbox__intnet: "aula_convivencia"
  end

  config.vm.define "Fernando" do |fernando|
    fernando.vm.hostname = "fernando"
    fernando.vm.network "private_network", mac: "0000c05dbd96", type: "dhcp", virtualbox__intnet: "aula_convivencia"
  end

end
