Vagrant.configure("2") do |config|

  config.vm.define "frederik-dockerhost" do |debian|
    debian.vm.box = "generic/ubuntu2310"
    debian.vm.network "public_network"
    debian.vm.network "private_network", ip: "10.10.10.130", virtualbox__intnet: "ansible_lab"
    debian.vm.hostname = "frederik-debian"
    debian.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "4096"]
      vb.customize ["modifyvm", :id, "--cpus", "4"]
      vb.name = "frederik-dockerhost"
    end
    debian.vm.provision "shell", inline: <<-SHELL
      # Ensure apt packages are up to date
      apt-get update
  
      # Install prerequisite packages
      apt-get install -y apt-transport-https ca-certificates curl software-properties-common
  
      # Add Docker’s official GPG key
      curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
  
      # Add Docker’s repository
      add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
  
      # Update package index again
      apt-get update
  
      # Install Docker
      apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    SHELL
  end
  
  

  config.vm.define "frederik-ansible" do |debian|
    debian.vm.box = "generic/ubuntu2304"
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
      apt-get install -y ansible tree sshpass yamllint ansible-lint
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
      vb.name = "frederik-ubuntu"
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
      yum update -y
      yum install -y fish tmux mc wget git
    SHELL
  end

  config.vm.define "frederik-opensuse" do |opensuse|
    opensuse.vm.box = "opensuse/Leap-15.2.x86_64"
    opensuse.vm.network "public_network"
    opensuse.vm.network "private_network", ip: "10.10.10.134", virtualbox__intnet: "ansible_lab"
    opensuse.vm.hostname = "frederik-opensuse"
    opensuse.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "frederik-opensuse"
    end
    opensuse.vm.provision "shell", inline: <<-SHELL
      zypper refresh
      zypper install -y fish tmux mc wget git
    SHELL
  end

end
