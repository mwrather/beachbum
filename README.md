# Drupal + Vagrant = Beachbum

Beachbum is a Vagrant- and Chef-powered development stack for Drupal Development.

## Using Beachbum

1. Install [Vagrant](http://www.vagrantup.com/) using one of the [package installers](http://downloads.vagrantup.com/).
2. Install the Vagrant [Berkshelf](http://berkshelf.com/) plugin: run `vagrant plugin install vagrant-berkshelf`
3. Clone this repo into a working directory
4. Run `vagrant up`
5. Enjoy a tasty beverage. Check progress. Enjoy another tasty beverage.
6. Run `vagrant ssh` to check out your virutal machine
7. Visit `http://192.168.232.24/` in your browser. (232-24 is BEA-CH on a phone keypad.) :)
8. Login to your drupal site with the username `admin` and the password `admin`.

To customize the site that beachbum installs, alter the `beachbum.make` file in the `www/` directory.