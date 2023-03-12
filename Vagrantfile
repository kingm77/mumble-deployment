Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  
  # Add a synced folder
  config.vm.synced_folder ".", "/vagrant"
  
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus = 2
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "deploy.yml"
    ansible.inventory_path = "inventory.ini"
  end
end

