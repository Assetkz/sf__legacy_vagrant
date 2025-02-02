Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y postgresql postgresql-contrib 
    sudo -u postgres createuser asset
    sudo -u postgres createdb -O asset testdb
    sudo adduser asset --gecos "" --disabled-password
    sudo usermod -aG sudo asset
    echo "123123\n123123" | sudo passwd asset
    echo "post123\npost123" | sudo passwd postgres
  SHELL
  config.vm.boot_timeout = 300
  config.vm.hostname = "Ubuntu20-postgres"
  config.vm.provider "virtualbox" do |vb|
    vb.name = "Ubuntu20-postgres-vm"
  end
end