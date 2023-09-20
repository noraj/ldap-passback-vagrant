# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/debian11"
  config.vm.network "public_network", bridge: "eth0"

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get -y install ldap-utils
    echo -e "slapd    slapd/internal/generated_adminpw    password admin\nslapd    slapd/password2    password admin\nslapd    slapd/internal/adminpw    password admin\nslapd    slapd/password1    password admin\n" | debconf-set-selections
    apt-get -y install slapd
    service slapd start
    echo olcSaslSecProps: noanonymous,minssf=0,passcred >> /etc/ldap/slapd.d/cn=config.ldif
    DEBIAN_FRONTEND=noninteractive apt-get -y install tshark
  SHELL
end
