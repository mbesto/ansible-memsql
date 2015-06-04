## Deploy MemSQL Community Edition on VirtualBox using Ansible

This lets you deploy an MemSQL Community Edition on a Linux Ubuntu Server 14.04 LTS using Vagrant to manage the VM and Ansible to deploy MemSQL to it. It's been tested on Mac OS X Yosemite.

### Prerequisites  

1. Install Ansible (I recommend `brew install ansible` if you're using Homebrew)
2. Install VirtualBox
3. 4GB Ram, 4 CPUs

### Instructions

1. Navigate to the main directory of this repo and execute `vagrant up`
2. This will run an Ansible playbook that will (a) create an Ubuntu VM (b) download MemSQL CE (c) extract and install it (d) install the MySQL driver
3. Confirm your VM is running by executing `ansible status`
4. Point your browser to `http://192.168.33.33:9000` and follow the [On-Premise Deployment instructions](http://docs.memsql.com/latest/setup/setup_onprem/)
5. SSH into your VM using `vagrant ssh` and execute `mysql -u root -h 127.0.0.1 -P 3306 --prompt="memsql> "` (refer to [How to Connect to MemSQL](http://docs.memsql.com/latest/concepts/connecting/) for more instructions) 

You should be able to see that MemSQL is running and that you can access the database via the MySQL client. You now have the ability to access a MemSQL database running in a VM. If you want to access it from your local machine, you can simply install the MySQL client and access it via the IP address like this: `mysql -u root -h 192.168.33.33 -P 3306`
