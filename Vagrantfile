Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"
  config.vm.hostname = "gp1f4a7blue.fjeclot.net"
  config.vm.provider "virtualbox" do |v|
    # v.gui = true
    v.name = "gp1f4a7blue"
    v.memory = 2048
    v.cpus = 2
    v.customize ['modifyvm', :id, '--clipboard', 'bidirectional','--groups','/ASIX2']
  end

  config.vm.network "public_network", type: "dhcp"


  config.vm.synced_folder "../codi", "/home/vagrant/gp1f4a7/codi"

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update -y
    # sudo apt-get upgrade -y
    sudo apt-get install -y aptitude net-tools git zip unzip
    sudo apt-get install -y apt-transport-https ca-certificates curl gnupg2 software-properties-common
    sudo curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"
    sudo apt-get -y update
    sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-compose
    sudo gpasswd -a vagrant docker
  SHELL

end
