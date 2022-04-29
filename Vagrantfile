Vagrant.configure("2") do |config|
  # master.
  config.vm.define "master" do |master|
    master.vm.box = "ubuntu/jammy64"
    master.vm.hostname = "master.test"
    master.vm.network :private_network, ip: "10.0.1.100"
	master.vm.network :private_network, ip: "172.25.1.100"
    master.vm.provision "shell",
      inline: "sudo apt update -y"
	master.ansible.playbook = "ubuntu.yml"
    master.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 2048]
      v.customize ["modifyvm", :id, "--cpus", 2]
      v.customize ["modifyvm", :id, "--vram", 12]
      v.customize ["modifyvm", :id, "--accelerate3d", "on"]
	end
  end
end