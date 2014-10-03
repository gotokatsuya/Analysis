# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Box 
  config.vm.box = "centos70"
  
  # R studio
  config.vm.network "forwarded_port", guest: 8787, host: 8787

  # Chef version
  config.omnibus.chef_version = :latest

  # Recipes
  config.vm.provision "chef_solo" do |chef|
    chef.cookbooks_path = ["./Analysis/berks-cookbooks", "./Analysis/site-cookbooks"]
    chef.run_list = [
        "recipe[yum]",
        "recipe[repo]",
        "recipe[mahout]",
        "recipe[rstudio::server]"
    ]
  end
end
