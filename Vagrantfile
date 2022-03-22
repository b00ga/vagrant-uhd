Vagrant.configure("2") do |config|
  config.vm.hostname = "uhd"

  config.vm.box = "bento/centos-stream-8"
  config.vm.synced_folder "shared-folder", "/vagrant"
  config.vm.synced_folder "playbooks", "/ansible", :mount_options => ["ro"]

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.galaxy_role_file = "requirements.yml"
    ansible.galaxy_roles_path = "/etc/ansible/roles"
    ansible.galaxy_command = "sudo ansible-galaxy role install -r %{role_file} --roles-path=%{roles_path} --force"
    ansible.provisioning_path = "/ansible"
    ansible.compatibility_mode = "2.0"
    ansible.verbose = '-vvv'
  end
end
