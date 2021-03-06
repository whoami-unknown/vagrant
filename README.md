# Ansible - Provisioning - Vagrant


### Ansible provisioning over EC2 instance:
    Ansible provisioning is used to configure and setup AWS EC2 instance using vagrant-aws plugin.

```bash
$ export AWS_KEY="AWS api key" AWS_SECRET="AWS secret key" KEY_NAME="AWS key pair name" KEY_PATH="AWS .pem key path"
$ vagrant plugin install vagrant-aws
$ vagrant box add dummy https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box
$ vagrant up --provider=aws
```

### Ansible provisioning over Local vagrant box:
Follow the following steps to configure local vagrant box using ansible provisioning:

```bash
$ vagrant box add ubuntu/trusty

Uncomment the following lines from `Vagrantfile`:


    Vagrant.require_version ">= 1.7.0"

    Vagrant.configure(2) do |config|

      config.vm.box = "ubuntu/trusty64"
      config.ssh.insert_key = false
      config.vm.network "private_network", ip: "192.168.5.1"
      
      config.vm.provision "ansible" do |ansible|
        ansible.verbose = "v"
        ansible.playbook = "ansible/playbook.yml"
      end

    end

$ vagrant up
```
