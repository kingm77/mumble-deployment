Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  
  # Add a synced folder
  config.vm.synced_folder ".", "/vagrant"
  
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus = 2
  end

  config.vm.network "client_port", guest: 3000, host: 3000
  config.vm.network "api_port", guest: 5000, host: 5000
  config.vm.network "pricer_port", guest: 34566, host: 34566
  config.vm.network "db_port", guest: 3306, host: 3307
  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "deploy2.yml"
    ansible.limit =  "all"
    ansible.inventory_path = "inventory.ini"
    ansible.install_mode = "pip"
    ansible.extra_vars = {
      project_src: "/vagrant"
    }
  end
end

