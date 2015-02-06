# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty32"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y --force-yes cmake git libxml-libxml-perl libxml-libxslt-perl mesa-common-dev build-essential zlib1g-dev
    cd /srv
    sudo git clone https://github.com/DFHack/dfhack.git
    cd /srv/dfhack
    sudo git submodule init
    sudo git submodule update
    cd /srv/dfhack/build
    sudo cmake .. -DCMAKE_BUILD_TYPE:string=Release -DCMAKE_INSTALL_PREFIX=/opt -Wno-dev
    sudo sed -i 's/BUILD_STONESENSE:BOOL=OFF/BUILD_STONESENSE:BOOL=ON/' /srv/dfhack/build/CMakeCache.txt
    sudo make install
    sudo rm -Rf /vagrant/dfhack
    mkdir -p /vagrant/dfhack
    sudo cp -r /opt/* /vagrant/dfhack
    sudo shutdown -h now
  SHELL
end
