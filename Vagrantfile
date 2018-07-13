Vagrant.configure(2) do |config|
  config.vm.box = "oleggorj/ubuntu-trusty64-docker"

  config.vm.provision "shell", inline: <<-SHELL
    cd /vagrant
    docker build  -t ansible:alpine3              alpine3
  SHELL
end



