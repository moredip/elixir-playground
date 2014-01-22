# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  
  config.vm.network :private_network, ip: "192.168.101.100"

  config.vm.provision :shell, :inline => PROVISION
end

PROVISION = <<EOP

if ! hash erl 2>/dev/null; then
  cd /tmp/
  wget http://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb
  dpkg -i erlang-solutions_1.0_all.deb
  
  apt-get update
  apt-get install -y esl-erlang
fi

if ! hash elixir 2>/dev/null; then
  apt-get install -y make

  cd /tmp
  rm -r elixir-stable
  wget -q -O - https://github.com/elixir-lang/elixir/archive/stable.tar.gz | tar xzv
  cd elixir-stable
  make && make install
fi

EOP
