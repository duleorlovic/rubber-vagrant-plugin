Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = false
  config.vm.network :private_network, ip: "192.168.70.10"

  # do not generate new key, copy my key and use it
  config.ssh.insert_key = false
  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
  config.ssh.private_key_path = ["~/.ssh/id_rsa", "~/.vagrant.d/insecure_private_key"]
  # ruby build fails on 512MB so we increase
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
  end

  config.vm.define "mysubdomain" do |tri|
  end

  config.vm.provision :rubber do |rubber|
    rubber.rubber_env = 'vagrant'

    # Only necessary if you use RVM locally.
    rubber.rvm_ruby_version = '2.3.3'
  end
end
