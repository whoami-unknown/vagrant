Vagrant.configure(2) do |config|

  config.vm.box = "dummy"
  config.vm.box_url = "https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box"  

  config.vm.provider :aws do |aws, override|
   aws.access_key_id = ENV['AWS_KEY']
   aws.secret_access_key = ENV['AWS_SECRET']
   aws.keypair_name = ENV['KEY_NAME']
   aws.ami = "ami-9abea4fb"
   aws.region = "us-west-2"
   aws.security_groups = [ 'vagrant' ]
   aws.instance_type = "t2.medium"
#  aws.elastic_ip = "x.x.x.x"
   override.vm.box = "dummy"
   override.ssh.username = "ubuntu"
   override.ssh.private_key_path = ENV['KEY_PATH']
  end

  config.vm.provision :shell, path: "bootstrap.sh"

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "ansible/playbook.yml"
  end

end

### Vagrant box for local developement ###
### vagrant box add ubuntu/trusty64 ###

# Vagrant.require_version ">= 1.7.0"

# Vagrant.configure(2) do |config|

#   config.vm.box = "ubuntu/trusty64"
#   config.ssh.insert_key = false
#   config.vm.network "private_network", ip: "192.168.5.1"
  
#   config.vm.provision "ansible" do |ansible|
#     ansible.verbose = "v"
#     ansible.playbook = "ansible/playbook.yml"
#   end

# end
