Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.box_check_update = false
  config.vm.hostname = "ubuntu-1404"
  config.vm.define "ubuntu-pgsql"
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "2048"
  end
  config.vm.provision "shell", inline: <<-SHELL
    echo "deb https://apt.postgresql.org/pub/repos/apt/ bionic-pgdg main" > /etc/apt/sources.list.d/pgdg.list
    wget --quiet -O - https://apt.postgresql.org/pub/repos/apt/ACCC4CF8.asc | apt-key add -
    apt update && apt upgrade
    export DEBIAN_FRONTEND=noninteractive
    apt install postgresql-8.4 -y
  SHELL
end
