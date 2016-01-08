# -*- mode: ruby -*-
# vi: set ft=ruby :
readynas_version="6.4.1"
Vagrant.configure(2) do |config|

  config.vm.box = "debian/wheezy64"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y git schroot debootstrap wget mc
    sudo mkdir -p /chroot/wheezy/mnt/src
    sudo debootstrap --arch amd64 wheezy /chroot/wheezy http://ftp.us.debian.org/debian
    sudo rsync -r /vagrant/provision/files/ /
    sudo sh -c "echo 'deb http://apt.readynas.com/packages/readynasos #{readynas_version} main dev' >> /chroot/wheezy/etc/apt/source.list"
    sudo schroot -c R6 apt-get -- install -y sudo
    schroot -c R6 sudo -- apt-get update
    schroot -c R6 sudo -- apt-get install -y build-essential \
    libcppunit-dev autoconf automake autotools-dev autopoint libtool \
    libxml2-dev libsqlite3-dev pkg-config libsystemd-daemon-dev
    sudo mount --bind -o umask=0,uid=vagrant,gid=vagrant /vagrant/src /chroot/wheezy/mnt/src
  SHELL
end
