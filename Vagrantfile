# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Use the stock vagrant precise32.box
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  # Forward port 8080 on the host to port 80 on the VM
  config.vm.network :forwarded_port, guest: 80, host: 8080

  # Create a private network, which allows host-only access at this IP
  # 232.24 is BEA.CH on a phone keypad
  config.vm.network :private_network, ip: "192.168.232.24"
  config.ssh.forward_agent = true

  # Set some Virtualbox settings
  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--memory", 2048]
    v.customize ["modifyvm", :id, "--name", "beachbum"]
  end

  # Sync the www folder with NFS
  config.vm.synced_folder "./www", "/var/www", id: "vagrant-root" , :nfs => true

  # We are using Chef Solo with Berkshelf http://berkshelf.com/
  # Install berkshelf with `vagrant plugin install berkshelf-vagrant`
  config.berkshelf.enabled = true

  # Provision with chef solo
  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "apt"
    chef.add_recipe "apache2"
    chef.add_recipe "php"
    chef.add_recipe "php::module_mysql"
    chef.add_recipe "php::module_gd"
    chef.add_recipe "apache2::mod_php5"
    chef.add_recipe "apache2::mod_rewrite"
    chef.add_recipe "apache2::mod_headers"
    chef.add_recipe "apache2::mod_expires"
    chef.add_recipe "openssl"
    chef.add_recipe "mysql::server"
    chef.add_recipe "build-essential"
    chef.add_recipe "beachbum-bonfire"

    chef.json = {
      "mysql" => {
        "server_root_password" => "root",
        "server_debian_password" => "root",
        "server_repl_password" => "root"
      },
      "hostname" => "beachbum.local",
      "set_env" => "dev"
    }
  end
end
