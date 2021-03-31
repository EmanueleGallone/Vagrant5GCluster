
ENV['VAGRANT_NO_PARALLEL'] = 'yes'

$k3s_token = %x[ openssl rand -hex 32 ]

#k3s master ip
master_ip = "192.168.56.2"

Vagrant.configure("2") do |config|

  #configure free5gc
  config.vm.define "hydrogen" do |h|
    h.vm.box = "bento/ubuntu-18.04"
    h.vm.hostname = 'hydrogen'
    #h.disksize.size = '50GB'
    #h.vm.box_url = "ubuntu/precise64"

    h.vm.network :private_network, ip: "192.168.56.1"

    h.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 8192]
      v.customize ["modifyvm", :id, "--name", "hydrogen"]
      v.cpus = 8
    end

    config.vm.provision "shell" , path: "provision-free5g.sh"
  end

  #configure k3s master
  config.vm.define "helium" do |h|
    h.vm.box = "bento/ubuntu-18.04"
    h.vm.hostname = 'helium'
    #h.disksize.size = '50GB'
    #h.vm.box_url = "ubuntu/precise64"

    h.vm.network :private_network, ip: master_ip, netmask: "255.255.255.0", auto_config: true

    h.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 2048]
      v.customize ["modifyvm", :id, "--name", "helium"]
      v.cpus = 4
    end

    h.vm.provision "shell", path: 'provision-master.sh', args: [$k3s_token, master_ip]
    h.vm.provision "shell", path: 'provision-traefik.sh'
  end

  #config agent
  config.vm.define "lithium" do |h|
    h.vm.box = "bento/ubuntu-18.04"
    h.vm.hostname = 'lithium'
    #h.disksize.size = '50GB'
    #h.vm.box_url = "ubuntu/precise64"
    private_ip = "192.168.56.3"

    h.vm.network :private_network, ip: private_ip, netmask: "255.255.255.0", auto_config: true

    h.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 2048]
      v.customize ["modifyvm", :id, "--name", "lithium"]
      v.cpus = 4
    end

    h.vm.provision "shell", path: 'provision-agent.sh', args: [$k3s_token, master_ip, private_ip]
  end


end
