# Drupal + Vagrant = Beachbum

Beachbum is a Vagrant- and Chef-powered development stack for Drupal Development.

## Using Beachbum

1. Install [Vagrant](http://www.vagrantup.com/) using one of the [package installers](http://downloads.vagrantup.com/).
2. Install the Vagrant [Berkshelf](http://berkshelf.com/) plugin: run `vagrant plugin install berkshelf-vagrant`
3. Clone this repo into a working directory
4. Run `vagrant up`
5. Enjoy a tasty beverage. Check progress. Enjoy another tasty beverage.
6. Run `vagrant ssh`
7. Visit `http://192.168.33.10/` in your browser.

Beachbum includes a sample drush makefile, and future versions will automatically configure the site.