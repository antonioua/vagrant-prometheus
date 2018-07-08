ENV["LC_ALL"] = "en_US.UTF-8"

image_path = "file:///home/kyrron/Downloads/CentOS-7-x86_64-Vagrant-1805_01.VirtualBox.box"
#image_path = "centos/7"
#nw_iface = "wlp2s0"

$nodes_amount = 2

Vagrant.configure("2") do |config|
  # v2 configs...

  # Sync time with the local host
  config.vm.provider 'virtualbox' do |vb|
    vb.customize [ "guestproperty", "set", :id, "/VirtualBox/GuestAdd/VBoxService/--timesync-set-threshold", 1000 ]
  end

  (1..$nodes_amount).each do |node|

    config.vm.define "vmka#{i}" do |vmka|
      vmka.vm.box = "#{image_path}"
      vmka.vm.hostname = "vmka-#{i}"
      ip = "10.10.10.#{10+i}"
      vmka.vm.network "private_network", ip: ip
      #vmka.vm.box_check_update = "false"

      vmka.vm.provider "virtualbox" do |vb|
        # Display the VirtualBox GUI when booting the machine
        vb.gui = false
        vb.memory = "3072"
        vb.cpus = 1
        vb.name = "vmka#{i}"
      end

    end

    vm.provision "shell", path: "https://example.com/provisioner.sh"

  end

end