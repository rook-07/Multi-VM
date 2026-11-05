
Vagrant.configure("2") do |config|

  # VM 1: Web Server 01
  config.vm.define "web01" do |web01|
    web01.vm.box = "bento/ubuntu-24.04"
    web01.vm.hostname = "web01"
    web01.vm.network "private_network", ip: "192.168.86.11"
  end

  # VM 2: Web Server 02
  config.vm.define "web02" do |web02|
    web02.vm.box = "bento/ubuntu-24.04"
    web02.vm.hostname = "web02"
    web02.vm.network "private_network", ip: "192.168.86.12"
  end

  # VM 3: Database Server
  config.vm.define "db01" do |db01|
    db01.vm.box = "cloud-image/rocky-9"
    db01.vm.hostname = "db01"
    db01.vm.network "private_network", ip: "192.168.86.13"

    # Provisioning for db01
    db01.vm.provision "shell", inline: <<-SHELL
      yum install -y wget unzip mariadb-server -y
      systemctl enable mariadb
      systemctl start mariadb
      dnf install -y httpd
      systemctl enable httpd
      systemctl start httpd
    SHELL
  end

end
