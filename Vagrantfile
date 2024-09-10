Vagrant.configure("2") do |config|

config.vm.define "frederik-dockerhost" do |debian|
    debian.vm.box = "generic/debian12"
    debian.vm.network "public_network"
    debian.vm.network "private_network", ip: "10.10.10.130", virtualbox__intnet: "ansible_lab"
    debian.vm.hostname = "frederik-debian"
    #debian.vm.synced_folder "./ansible_data", "/vagrant_data"
    debian.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "4096"]
    vb.customize ["modifyvm", :id, "--cpus", "4"]
  vb.name = "frederik-dockerhost"
    end
  debian.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y fish tmux mc wget git
    apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  SHELL
end
config.vm.define "frederik-ansible" do |debian|
    debian.vm.box = "generic/debian12"
    debian.vm.network "public_network"
    debian.vm.network "private_network", ip: "10.10.10.131", virtualbox__intnet: "ansible_lab"
    debian.vm.hostname = "frederik-ansible"
    debian.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--cpus", "4"]
  vb.name = "frederik-ansible"
    end
  debian.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y fish tmux mc wget git
    apt-get install Ansible tree sshpass yamllint ansible-lint
  SHELL
end
config.vm.define "frederik-ubuntu" do |ubuntu|
    ubuntu.vm.box = "bento/ubuntu-24.04"
    ubuntu.vm.network "public_network"
    ubuntu.vm.network "private_network", ip: "10.10.10.132", virtualbox__intnet: "ansible_lab"
    ubuntu.vm.hostname = "frederik-ubuntu"
    ubuntu.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
  vb.name = "frederik-UBUNTU"
    end
  ubuntu.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y fish tmux mc wget git
  SHELL
end
config.vm.define "frederik-centos" do |centos|
    centos.vm.box = "generic/centos9s"
    centos.vm.network "public_network"
    centos.vm.network "private_network", ip: "10.10.10.133", virtualbox__intnet: "ansible_lab"
    centos.vm.hostname = "frederik-centos"
    centos.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
  vb.name = "frederik-centos"
    end
  centos.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y fish tmux mc wget git
  SHELL
end
config.vm.define "frederik-opensuse" do |opensuse|
    opensuse.vm.box = "opensuse/Leap-15.2.x86_64"
    opensuse.vm.network "public_network"
    opensuse.vm.network "private_network", ip: "10.10.10.133", virtualbox__intnet: "ansible_lab"
    opensuse.vm.hostname = "frederik-centos"
    opensuse.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
  vb.name = "frederik-opensuse"
    end
  opensuse.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y fish tmux mc wget git
  SHELL
end
end