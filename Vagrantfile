Vagrant.configure("2") do |config|
  config.vm.define "vm2" do |node|
    node.vm.box = "rockylinux/9"
    node.vm.hostname = "database"
    node.vm.network "private_network", ip: "10.0.1.12"
  end

  config.vm.define "vm3" do |node|
    node.vm.box = "rockylinux/9"
    node.vm.hostname = "dbadmin"
    node.vm.network "private_network", ip: "10.0.1.13"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "database.yml"
    ansible.inventory_path = "hosts"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "dbadmin.yml"
    ansible.inventory_path = "hosts"
  end

  config.vm.synced_folder ".", "/vagrant", disabled: true
end
