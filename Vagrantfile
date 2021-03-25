
#UNDER DEVELOPMENT

Vagrant.configure("2") do |config|
  config.vm.define "hydrogen" do |h|
    h.vm.box = "bento/ubuntu-18.04"
    h.vm.hostname = 'hydrogen'
    h.disksize.size = '50GB'
    #h.vm.box_url = "ubuntu/precise64"

    h.vm.network :private_network, ip: "192.168.56.1"

    h.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 8192]
      v.customize ["modifyvm", :id, "--name", "hydrogen"]
      v.cpus = 8
    end
  end


  config.vm.define "helium" do |h|
    h.vm.box = "bento/ubuntu-18.04"
    h.vm.hostname = 'helium'
    h.disksize.size = '50GB'
    #h.vm.box_url = "ubuntu/precise64"

    h.vm.network :private_network, ip: "192.168.56.2"

    h.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 2048]
      v.customize ["modifyvm", :id, "--name", "helium"]
      v.cpus = 4
    end
  end

  config.vm.define "lithium" do |h|
    h.vm.box = "bento/ubuntu-18.04"
    h.vm.hostname = 'lithium'
    h.disksize.size = '50GB'
    #h.vm.box_url = "ubuntu/precise64"

    h.vm.network :private_network, ip: "192.168.56.3"

    h.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 2048]
      v.customize ["modifyvm", :id, "--name", "lithium"]
      v.cpus = 4
    end
  end

end
