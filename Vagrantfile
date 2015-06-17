 -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  #config.vm.box = "ubuntu/trusty64"
  config.vm.box = "packer_amazon-ebs_aws.box"
  #config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  #config.vm.network "forwarded_port", guest: 3306, host: 3306
  #config.vm.network "private_network", ip: "192.168.33.10"
  #config.ssh.forward_agent = true
  
  config.vm.provider :aws do |aws, override|
    aws.access_key_id = '*******'      # Replace this
    aws.secret_access_key = '*******'  # Replace this
    aws.keypair_name = 'mykey'       # Replace this
    aws.ami = 'ami-ffcef4cf'        # ubuntu 12.04
    override.ssh.username = 'ubuntu'
    override.ssh.private_key_path = '/home/bob/Moved.pem'
  end
  config.vm.provider "virtualbox" do |vb|
     vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.verbose = "vv"
    ansible.sudo = true
  end
end
