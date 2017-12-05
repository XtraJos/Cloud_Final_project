
	# encoding: utf-8
	
	nodes = [
  { :hostname => 'web1', :ip => '192.168.1.3', :box => 'ubuntu/trusty64' },
  { :hostname => 'web2', :ip => '192.168.1.4', :box => 'ubuntu/trusty64' },
]
	
	
	Vagrant.configure("2") do |config|
		
	#  config.vm.synced_folder ".", "/vagrant", disabled: false
	  (1..2).each do |i|
	    config.vm.define "web#{i}" do |node|
	        nodeconfig.vm.box = "ubuntu/trusty64"
			nodeconfig.vm.hostname = node[:hostname] + ".box"
			nodeconfig.vm.network :private_network, ip: node[:ip]
	        end		
		end
	  end
	
	  # create load balancer
	  config.vm.define :lb do |lb_config|
	      lb_config.vm.box = "ubuntu/trusty64"
	      lb_config.vm.hostname = "lb"
	      lb_config.vm.network :private_network, :ip => "192.168.1.1"
		  lb_config.vm.provision "update",type:"shell",path: "bootstrap2.sh"
	      end   
	  end
	  # create mgmt node
	  config.vm.define :mgmt do |mgmt_config|
	      mgmt_config.vm.box = "ubuntu/trusty64"
	      mgmt_config.vm.hostname = "mgmt"
	      mgmt_config.vm.network :private_network, :ip => "192.168.1.2" 
	        vb.memory = "2048"
	      end  
	  end
	
	end