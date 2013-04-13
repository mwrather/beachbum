# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Use the stock vagrant precise32.box
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  # Forward port 8080 on the host to port 80 on the VM
  config.vm.network :forwarded_port, guest: 80, host: 8080

  # Create a private network, which allows host-only access at this IP
  config.vm.network :private_network, ip: "192.168.33.10"

  # Share additional folders
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provision with chef solo
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "chef/cookbooks"
    chef.roles_path = "chef/roles"
    # chef.data_bags_path = "chef/data_bags"

    # Add Recipes and Roles (we're adding recipes in the role definition)
    # chef.add_recipe "mysql"
    chef.add_role("beachbum")

    # You can specify JSON attributes here or in the role definition.
    # chef.json = { :mysql_password => "foo" }
  end
end
