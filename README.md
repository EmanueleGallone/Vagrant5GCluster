Providing an emulated MEC (Mobile edge computing) environment through vagrant.

# Getting Started
git clone this repository.

in provision-free5g.sh, Edit: 
* The $INTERFACE variable, pointing to the name of the interface that provides internet connection.
* The root password used by ansible-playbook (within the --extra-vars argument)

Then
```
vagrant up
```

SSH to the free5gc vm
```
vagrant ssh hydrogen
```

Verify that free5gc containers are running
```
sudo docker ps
```

Connect to the UE container
```
sudo docker exec -it ue bash
```

List all the UEs
```
ifconfig
```

Verify the connection to internet
```
ping 8.8.8.8 -I oaitun_ue1
```


# Warning
Setting up the VMs will take approximately ~ 15-20 minutes.


# External links
* Free5gc vm setup scripts [link](https://github.com/LABORA-INF-UFG/NetSoft2020-Tutorial4-Demo2-Exp1)

* Vagrant provision scripts partially forked from [randy-stad](https://github.com/randy-stad/k3s-vagrant-cluster/)

