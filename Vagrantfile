Vagrant::Config.run do |config|
  config.vm.box = "precise64"

  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.forward_port 8080, 8080

  config.vm.share_folder "app", "/home/vagrant/app", "app"

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "nodejs"
    chef.json = {
      "nodejs" => {
        "version" => "0.12.0"
      }
    }
  end

  config.vm.provision :shell, :inline => "sudo apt-get install -y build-essential --no-install-recommends"
  config.vm.provision :shell, :inline => "sudo apt-get install -y git --no-install-recommends"
  config.vm.provision :shell, :inline => "sudo npm install -g gulp"
end
