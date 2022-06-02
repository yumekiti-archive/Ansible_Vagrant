Vagrant.require_version ">= 1.8.0"

Vagrant.configure(2) do |config|

  config.vm.box = "generic/ubuntu2004"

  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.synced_folder "./", "/home/vagrant/ansible/", create:"true"

  config.vm.provision :shell, :inline => <<-EOS
    /etc/apt/sources.list >> deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
    sudo apt update
    sudo apt -y install ansible
    sudo ansible-playbook /home/vagrant/ansible/playbook.yml
  EOS

end