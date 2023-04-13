# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
        config.vm.box = "centos/7"
        config.vm.define "server" do |server|
            server.vm.hostname = "server"
            server.vm.network "private_network", ip: "192.168.56.160"
            server.vm.provider :virtualbox do |vb|
                disk2 = 'disk2.vdi'
                if !File.exist?(disk2)
                        vb.customize ['createhd', '--filename', disk2, '--size', 2 * 1024]
                end
                vb.customize ['storageattach', :id, '--storagectl', 'IDE', '--port', '0', '--device', '1', '--type', 'hdd', '--medium', disk2]
            end

        end
        config.vm.define "client" do |client|
            client.vm.hostname = "client"
            client.vm.network "private_network", ip: "192.168.56.150"
        end
    end