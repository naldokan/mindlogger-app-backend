Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.define "girder"

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
    config.cache.enable :apt
    config.cache.enable :npm
  end

  config.vm.hostname = "girder"

  config.vm.network "forwarded_port", guest: 8080, host: 9080
  config.vm.post_up_message = "Girder is running at http://localhost:9080"

  config.vm.synced_folder ".", "/vagrant", disabled: true
  #config.vm.synced_folder ".", "/home/vagrant/girder"

  config.vm.provision "ansible" do |ansible|
    client_testing = ENV["ANSIBLE_CLIENT_TESTING"] || false
    if client_testing then
      ansible.playbook = "devops/ansible/roles/girder/library/test/site.yml"
      ansible.galaxy_role_file = "devops/ansible/roles/girder/library/test/requirements.yml"
    else
      example = ENV["GIRDER_EXAMPLE"] || "girder-dev-environment"
      ansible.playbook = "devops/ansible/examples/#{example}/site.yml"
      ansible.galaxy_role_file = "devops/ansible/examples/#{example}/requirements.yml"
    end
  end

  config.vm.provider "virtualbox" do |virtualbox|
    virtualbox.name = "girder"
    virtualbox.memory = 2048
  end
end
