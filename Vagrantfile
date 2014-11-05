Vagrant.configure("2") do |config|

    config.vm.box = "debian-770-amd64-vbox4318"
    config.vm.box_url = "debian-770-amd64-vbox4318.box"

    config.ssh.forward_agent = true
    config.ssh.pty = false

    #config.vm.synced_folder "./www", "/home/admin/www", owner: "admin", group: "www-data", mount_options: ["dmode=775","fmode=664"]
    #config.vm.synced_folder "./www", "/home/admin/www", owner: "admin", group: "www-data", mount_options: ["dmode=775","fmode=664"], type: "rsync", rsync__exclude: ".git/"
    #config.vm.synced_folder "./www", "/home/admin/www", type: "nfs", nfs_version: 3, nfs_udp: false

    config.vm.provider :virtualbox do |v|
        v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        v.customize ["modifyvm", :id, "--memory", 2048]
        v.customize ["modifyvm", :id, "--cpus", 2]
    end

    config.vm.provision :puppet do |puppet|
        puppet.manifests_path = "puppet/manifests"
        puppet.module_path    = "puppet/modules"
        puppet.options        = [
            #'--debug',
            #'--verbose',
            '--hiera_config /vagrant/puppet/hiera.yaml',
            '--parser=future'
            ]

        config.vm.define "jeuxdicode", primary: true do |jeuxdicode|
            jeuxdicode.vm.hostname = 'jeuxdicode.dev'
            jeuxdicode.vm.network :private_network, ip: "192.168.50.20"

            jeuxdicode.vm.provider :virtualbox do |v|
                v.customize ["modifyvm", :id, "--name", "JeUXdiCode"]
            end

            puppet.facter = {
                "fqdn" => "jeuxdicode.dev",
                "env" => "dev",
                "roles" => "web,db,app,cache",
                "cluster" => "jeuxdicode",
                "hieradata_dir" => "/vagrant/puppet/hieradata"
            }
        end
    end
end
