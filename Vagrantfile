require 'vagrant-openstack-provider'

Vagrant.configure('2') do |config|


  config.ssh.username = ENV['OS_SSH_USERNAME']

  config.vm.provider :openstack do |os|
    os.username           = ENV['OS_USERNAME']
    os.password           = ENV['OS_PASSWORD']
    os.flavor             = "GP-Large"
    os.image              = "trusty-server-cloudimg-amd64-disk1.2015-01-27"
    os.openstack_auth_url = "https://us-rdu-1.cisco.com:5000/v2.0/tokens"
    os.openstack_network_url = "https://us-rdu-1.cisco.com:9696/v2.0"
    os.openstack_image_url = "https://us-rdu-1.cisco.com:9292/v2.0"
    os.openstack_volume_url = "https://us-rdu-1.cisco.com:8776/v1/e7e394f0992d47c7ab8342842f573d5c"
    os.tenant_name        = ENV['OS_TENANT_NAME']
    os.sync_method        = 'none'
    #os.networks           = "fdce48ad-7707-4b53-8fc7-86d1cbf041cc"
    os.ssh_disabled = "true"
    os.keypair_name = "messenger-infra"


  end

#Boot ubuntu machines

(1..4).each do |i|
    config.vm.define "instance_#{i}" do |instance|
      instance.vm.provider :openstack do |os|
        os.server_name      = "ubuntu-#{i}"
        os.networks           = {id: 'fb33532b-3f26-4d77-8f0b-f2b89c851e87', address: "192.168.0.2#{i}" }
        #os.floating_ip_pool = ENV['OS_FLOATING_IP_POOL']
      end
    end
  end
end
