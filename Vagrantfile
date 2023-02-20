# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.define "nxos1" do |node|
    config.vm.box = "nexus9300v.9.3.10"

    config.vm.network :forwarded_port, guest: 22, host: 3022, id: 'ssh', auto_correct: true
    config.vm.network :forwarded_port, guest: 80, host: 3080, id: 'http', auto_correct: true
    # enable "feature nxapi", browse to "https://localhost:3443/"
    config.vm.network :forwarded_port, guest: 443, host: 3443, id: 'https', auto_correct: true
    config.vm.network :forwarded_port, guest: 830, host: 3830, id: 'netconf', auto_correct: true
    config.vm.network :forwarded_port, guest: 161, host: 3161, protocol: 'udp', id: 'snmp', auto_correct: true

    config.vm.network :private_network, virtualbox__intnet: "link2", auto_config: false
  end
  config.ssh.shell = "run bash"

  #config.vm.boot_timeout = 1800

  #if VAGRANT_COMMAND = "up"
  #  config.ssh.shell = "conf t ; hostname helloworld ; copy r s"
  #end
  #config.vm.guest = :freebsd

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
#     vb.gui = true
     vb.cpus = "2"
     vb.memory = "8192"
     vb.customize ["modifyvm", :id, "--firmware", "efi"]
     # telnet console, usually on tcp 2023
     vb.customize ["modifyvm", :id, "--uart1", "0x3F8", "4"]
    end

end
