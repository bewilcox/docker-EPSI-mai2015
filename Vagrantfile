VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.hostname ="docker-epsi"

  config.vm.provision :shell, :inline => "sudo apt-get update"

  # Docker installation
  config.vm.provision :shell, :inline => "sudo apt-get install -y curl; curl -s http://get.docker.io/ubuntu/ | sudo sh"

  # Add vagrant to the docker user group
  config.vm.provision :shell, :inline => "sudo gpasswd -a vagrant docker"
  config.vm.provision :shell, :inline => "sudo service docker restart"

  # Docker compose installation
  config.vm.provision :shell, :inline => "curl -L https://github.com/docker/compose/releases/download/1.1.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose"
  config.vm.provision :shell, :inline => "chmod +x /usr/local/bin/docker-compose"
  config.vm.provision :shell, :inline => "curl -L https://raw.githubusercontent.com/docker/compose/1.1.0/contrib/completion/bash/docker-compose > /etc/bash_completion.d/docker-compose"

  # Uncomment to map ports with the localhost
  #config.vm.network :forwarded_port, guest: 5000, host: 5000
end
