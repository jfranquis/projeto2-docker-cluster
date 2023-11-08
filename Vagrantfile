machines = {
  "node01" => {"memory" => "1024", "cpu" => "1", "image" => "bento/ubuntu-22.04"},
  "node02" => {"memory" => "1024", "cpu" => "1", "image" => "bento/ubuntu-22.04"},
  "node03" => {"memory" => "1024", "cpu" => "1", "image" => "bento/ubuntu-22.04"},
  "node04" => {"memory" => "1024", "cpu" => "1", "image" => "bento/ubuntu-22.04"}
}

Vagrant.configure("2") do |config|

  machines.each do |name, conf|
    config.vbguest.installer_options = { foo: 1, bar: 2 }
    config.vbguest.auto_update = false
    config.vbguest.no_remote = true
    config.vm.define "#{name}" do |machine|
      machine.vm.box = "#{conf["image"]}"
      machine.vm.hostname = "#{name}"
      machine.vm.network "public_network"
      machine.vm.provider "virtualbox" do |vb|
        vb.name = "#{name}"
        vb.memory = conf["memory"]
        vb.cpus = conf["cpu"]
        
      end
      machine.vm.provision "shell", path: "install-docker.sh"   
    end
  end
end

