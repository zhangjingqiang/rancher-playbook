Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.3"
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--memory", 512]
  end

  # Rancher Server
  config.vm.define "rancherserver_centos", primary: true do |host|
    host.vm.hostname = 'rancherserver'
    host.vm.network :private_network, ip: "192.168.33.111"
    host.vm.network :forwarded_port, guest: 22, host: 1234, id: 'ssh'
  end

  # Rancher Agent1
  config.vm.define "rancheragent1_centos" do |host|
    host.vm.hostname = 'rancheragent1'
    host.vm.network :private_network, ip: "192.168.33.112"
    host.vm.network :forwarded_port, guest: 22, host: 1235, id: 'ssh'
  end

  # Rancher Agent2
  config.vm.define "rancheragent2_centos" do |host|
    host.vm.hostname = 'rancheragent2'
    host.vm.network :private_network, ip: "192.168.33.113"
    host.vm.network :forwarded_port, guest: 22, host: 1236, id: 'ssh'
  end
end
