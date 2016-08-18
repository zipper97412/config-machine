Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.define "node1" do |machine|
    machine.vm.network "private_network", ip: "172.17.177.21"
  end

  # config.vm.define "node2" do |machine|
    # machine.vm.network "private_network", ip: "172.17.177.22"
  # end

  config.vm.define 'controller' do |machine|
    machine.vm.network "private_network", ip: "172.17.177.11"

    machine.vm.provision :ansible_local do |ansible|
      ansible.playbook       = "playbook.yml"
      ansible.verbose        = true
      ansible.install        = true
      ansible.limit          = "all" # or only "nodes" group, etc.
      ansible.inventory_path = "inventory"
	  ansible.extra_vars = { ansible_ssh_user: 'vagrant', ansible_ssh_pass: 'vagrant'}
    end
  end

end
