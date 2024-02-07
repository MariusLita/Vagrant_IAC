This project is using vagrant utility in order to provisioning a local ubuntu and centos VM which host an appache and httpd server.

Prerequisites:
- Vagrant : it can be downloaded and installed from the official website https://developer.hashicorp.com/vagrant/install
- VirtualBox : it can be downloaded and installed from the official website https://www.virtualbox.org/wiki/Downloads
- Git utility : https://git-scm.com/downloads

If you are familiar with chocolatey you can use that package manager to install the required softwares.

The project contains three branched 

- master branch which have the README file with the project details.
- ubuntu branch which have the Vagrantfile for the ubuntu VM
- centos branch which have the Vagrantfile for the centos VM


Details about ubuntu provisioning
	The Vagranfile contains the basic configuration like:
		- private ip : 192.168.56.30
		- configured public_network in bridge mode.
		- using the default provider which is virtualbox
		- RAM memory ~1.5GB
		- the provisioning for the WordPress and it's dependecies ( like apache , sql , etc )
		- installation of the WordPress was done from the offical website : https://ubuntu.com/tutorials/install-and-configure-wordpress
		- After the provisioning will be complete just run the private ip ( 192.168.56.30 ) on the browser and you should be able to see the WordPress system.
	
Details about centos provi
	The Vagrantfile contain the basic configuration like:
		- private ip : 192.168.56.28
		- configured public_network in bridge mode.
		- using the default provider which is virtualbox
		- RAM memory ~1GB
		- instalation for the http and it's dependecies.
		- since http is just running a simple html template. I used https://www.tooplate.com/view/2135-mini-finance to get a template for a finance page.
		- After the provisioning will be complete just run the private ip ( 192.168.56.28 ) on the browser and you should be able to finance webpage.
	
Steps to run the project.

	git clone https://github.com/MariusLita/Vagrant_IAC.git

	cd <repository> - it should be Vagrant_IAC

Here you should see the README file.

	git checkout ubuntu - switch to ubuntu branch
	mkdir ubuntu - create a new directory for the ubuntu vagrant file
	cp Vagrantfile ubuntu/ - copy the Vagrantfile to the ubuntu directory

	git checkout centos - switch to centos branch
	mkdir centos - create a new directory for the centos vagrant file
	cp Vagrantfile centos/ - copy the Vagrantfile to the centos directory

At this point you will have two directories ( ubuntu and centos ) and the README file.

If you want to start the ubuntu vm:
	cd ubuntu/
	vagrant up
	
After the provisioning will be complete just go on a browser and type 192.168.56.30

If you want to start the centos vm:
	cd centos/
	vagrant up

After the provisioning will be complete just go on a browser and type 192.168.56.28

Both the Vagrantfiles are similiar. For the ubuntu it is using apache2 and for centos it is using httpd.
Since Vagrant is an utility for local provisioning, two separate directories were required for each specific VM.

After you powering up both VM or just one based on your needs, you can use :
    vagrant global-status - to check the status of the VM

It is recommended to destroy or shutting down the VM:
    vagrant halt - shut down the VM
    vagrant destroy - delete the VM
