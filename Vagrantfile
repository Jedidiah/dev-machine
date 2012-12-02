# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "dev-box"
  config.vm.box_url = "http://dl.dropbox.com/u/1537815/precise64.box"

  config.vm.share_folder "bridge", "/home/vagrant/bridge", File.expand_path("./bridge")

  config.ssh.forward_agent = true
  config.vm.network :hostonly, "192.168.33.10"
  config.vm.customize [
    "modifyvm", :id,
    "--memory", (1 * 1024).to_s,
    "--cpus", 2]
  #
  # Enable provisioning with chef solo, specifying a cookbooks path, roles
  # path, and data_bags path (all relative to this Vagrantfile), and adding
  # some recipes and/or roles.
  #
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path     = "cookbooks"
    chef.roles_path         = "roles"
    chef.add_role             "devbox"
  end
end