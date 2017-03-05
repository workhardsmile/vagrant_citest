# -*- mode: ruby -*-
# vi: set ft=ruby :
# usage: vagrant up --provision
# ubuntu + nginx + php5.6 + ruby1.9.3(TestPlus+TestLink+Jenkins)

Vagrant.configure(2) do |config|
  hostname = "ubuntu14"
  config.vm.define hostname do |node|
    node.vm.hostname = hostname
    node.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.gui = false
    end
    node.vm.box = "ubuntu_trusty64"
    # config.vm.box_url = 'http://192.168.29.158/ubuntu_trusty64.box'
    node.vm.network "forwarded_port", guest: 80, host: 8000
    node.vm.network "forwarded_port", guest: 8001, host: 8001
    node.vm.network "forwarded_port", guest: 8002, host: 8002
    node.vm.network "forwarded_port", guest: 8003, host: 8003
    node.vm.network "forwarded_port", guest: 8004, host: 8004
    node.vm.network "forwarded_port", guest: 8005, host: 8005
    # node.vm.network "private_network", ip: "192.168.42.42"
    node.vm.synced_folder "opt", "/tmp/opt"
    node.vm.provision "file", source: "nginx-vhost.conf", destination: "/tmp/nginx-vhost.conf"
    node.vm.provision "shell", inline: <<-SHELL
        sudo bash
        add-apt-repository -y ppa:webupd8team/java
        add-apt-repository -y ppa:ondrej/php
        apt-get update
        #apt-get install oracle-java8-installer
        #update-java-alternatives -s java-8-oracle&&java -version
        #apt-get install libcurl4-openssl-dev build-essential bison openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev  libxml2-dev libxslt-dev autoconf libc6-dev zlib1g-dev libssl-dev build-essential curl git-core libc6-dev g++ gcc
        #apt-get install mysql-server mysql-client libmysqlclient-dev redis-server 
        #apt-get install -y php5.6 php5.6-fpm php5.6-mbstring php5.6-xml mcrypt php5.6-mcrypt php5-mysql unzip 
        #apt-get purge graphicsmagick graphicsmagick-dbg imagemagick-common imagemagick libmagickwand-dev
        #apt-get install docker.io imagemagick libmagickwand-dev 
        #ln -sf /usr/bin/docker.io /usr/local/bin/docker
        #useradd -m railsu
        #useradd -m passenger
        #useradd -m www-data
        #usermod -G passenger,www-data,sudo railsu
        #su - railsu && curl -L get.rvm.io | bash -s stable
        #source /home/railsu/.rvm/scripts/rvm
        #rvm install 1.9.3 && rvm use 1.9.3 default
        #gem sources --add "https://ruby.taobao.org/"        
        #gem install rack -v 1.4.7 && gem install passenger
        #rvmsudo passenger-install-nginx-module
        #mkdir -p /var/log/nginx
        #ln -sf /opt/nginx/sbin/nginx /usr/local/bin/nginx
        #wget -q -O - http://pkg.jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add - 
        #sh -c 'echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list'
        #apt-get install jenkins -y
    SHELL
  end
end