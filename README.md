Vagrant file for Free RADIUS server.
===================================

This is vagrant file for installing [FreeRADIUS](http://freeradius.org/) server with mysql as authorization data storage on Ubuntu 14.04 64 bit.

Commands for installing server and configuring it are in **provisioner** file. Commands install freeradius and mysql. After installation, database is created and sql is enabled inside freeradius config files.


Installation
===================================

If you know vagrant and have it already installed you just need to clone this repo in a folder on your system and run `vagrant up` inside folder to set up the VM.

If you don't want to use vagrant for some reason, download ubuntu 14.04 iso, setup a VM in virtualbox, vmware or kvm or any other hypervisor. Copy content of file `provisioner` in any file inside vm and execute it with sudo.

Testing
====================================
If everything goes well, ssh into the vm and run following to verify:

`radtest bob passbob 127.0.0.1 100 testing123`

#####Expected Output:

```
Sending Access-Request of id 242 to 127.0.0.1 port 1812
	User-Name = "bob"
	User-Password = "passbob"
	NAS-IP-Address = 127.0.1.1
	NAS-Port = 100
	Message-Authenticator = 0x00000000000000000000000000000000
rad_recv: Access-Accept packet from host 127.0.0.1 port 1812, id=242, length=32
	Reply-Message = "Hello Bob!"
```