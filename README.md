Providing an emulated MEC (Mobile edge computing) environment through vagrant.

# Getting Started
git clone this repository. Then
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



# Warning
Setting up the VMs will take approximately ~ 15-20 minutes.


# External links
* Free5gc vm setup scripts [link](https://github.com/LABORA-INF-UFG/NetSoft2020-Tutorial4-Demo2-Exp1)

* Vagrant provision scripts partially forked from [randy-stad](https://github.com/randy-stad/k3s-vagrant-cluster/)

