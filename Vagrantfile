# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "hashicorp/precise32"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  # config.ssh.forward_agent = true

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Don't boot with headless mode
  #   vb.gui = true
  #
  #   # Use VBoxManage to customize the VM. For example to change memory:
  #   vb.customize ["modifyvm", :id, "--memory", "1024"]
  # end
  #
  # View the documentation for the provider you're using for more
  # information on available options.

  # Enable provisioning with CFEngine. CFEngine Community packages are
  # automatically installed. For example, configure the host as a
  # policy server and optionally a policy file to run:
  #
  # config.vm.provision "cfengine" do |cf|
  #   cf.am_policy_hub = true
  #   # cf.run_file = "motd.cf"
  # end
  #
  # You can also configure and bootstrap a client to an existing
  # policy server:
  #
  # config.vm.provision "cfengine" do |cf|
  #   cf.policy_server_address = "10.0.2.15"
  # end

  # Enable provisioning with Puppet stand alone.  Puppet manifests
  # are contained in a directory path relative to this Vagrantfile.
  # You will need to create the manifests directory and a manifest in
  # the file default.pp in the manifests_path directory.
  #
  # config.vm.provision "puppet" do |puppet|
  #   puppet.manifests_path = "manifests"
  #   puppet.manifest_file  = "site.pp"
  # end

  # Enable provisioning with chef solo, specifying a cookbooks path, roles
  # path, and data_bags path (all relative to this Vagrantfile), and adding
  # some recipes and/or roles.
  #
  # config.vm.provision "chef_solo" do |chef|
  #   chef.cookbooks_path = "../my-recipes/cookbooks"
  #   chef.roles_path = "../my-recipes/roles"
  #   chef.data_bags_path = "../my-recipes/data_bags"
  #   chef.add_recipe "mysql"
  #   chef.add_role "web"
  #
  #   # You may also specify custom JSON attributes:
  #   chef.json = { :mysql_password => "foo" }
  # end

  # Enable provisioning with chef server, specifying the chef server URL,
  # and the path to the validation key (relative to this Vagrantfile).
  #
  # The Opscode Platform uses HTTPS. Substitute your organization for
  # ORGNAME in the URL and validation key.
  #
  # If you have your own Chef Server, use the appropriate URL, which may be
  # HTTP instead of HTTPS depending on your configuration. Also change the
  # validation key to validation.pem.
  #
  # config.vm.provision "chef_client" do |chef|
  #   chef.chef_server_url = "https://api.opscode.com/organizations/ORGNAME"
  #   chef.validation_key_path = "ORGNAME-validator.pem"
  # end
  #
  # If you're using the Opscode platform, your validator client is
  # ORGNAME-validator, replacing ORGNAME with your organization name.
  #
  # If you have your own Chef Server, the default validation client name is
  # chef-validator, unless you changed the configuration.
  #
  #   chef.validation_client_name = "ORGNAME-validator"
end

$buildStructures = <<SCRIPT
echo Building Structures
sudo apt-get -y update
sudo apt-get -y install default-jre
sudo apt-get -y dist-upgrade
# I must have the one true editor
sudo apt-get -y install emacs
sudo apt-get -y install unzip
sudo apt-get -y install default-jre
sudo a2enmod rewrite
sudo apt-get -y install libapache2-mod-wsgi
sudo service apache2 restart
sudo apt-get -y install python-pip
sudo pip install requests
sudo pip install bottle
sudo pip install solrpy
if [ ! -d "PriceHistory" ]; then
  # Control will enter here if $DIRECTORY doesn't exist.
   mkdir PriceHistory
fi
# We will want to fix all this up at the end...
sudo chown www-data.www-data -R PriceHistory
cd PriceHistory
if [ ! -d "configuration" ]; then
  # Control will enter here if $DIRECTORY doesn't exist.
   mkdir configuration
fi
if [ ! -d "logs" ]; then
  # Control will enter here if $DIRECTORY doesn't exist.
   mkdir logs
fi
sudo chmod o+w -R logs
sudo apt-get -y install git
if [ ! -d "PriceHistoryGUI" ]; then
   sudo git clone https://github.com/18F/PriceHistoryGUI.git
fi
if [ ! -d "PriceHistoryAPI" ]; then
   sudo git clone https://github.com/18F/PriceHistoryAPI.git
fi
if [ ! -d "PriceHistoryAuth" ]; then
   sudo git clone https://github.com/18F/PriceHistoryAuth.git
fi
if [ ! -d "MorrisDataDecorator" ]; then
   sudo git clone https://github.com/18F/MorrisDataDecorator.git
fi
SCRIPT

$copyFiles = <<SCRIPT
echo Installing Particular Files
sudo chown www-data.www-data -R PriceHistory
cp p3api.hashes.txt PriceHistory/configuration
cd PriceHistory
unzip -o /home/vagrant/js.zip
unzip -o /home/vagrant/cookedData.zip
unzip -o /home/vagrant/SlickGrid-master.zip
unzip -o /home/vagrant/solr-4.7.2.zip
cp /home/vagrant/schema.PriceHistory.xml /home/vagrant/PriceHistory/solr-4.7.2/example/solr/collection1/conf/schema.xml
touch __init__.py
bash PriceHistoryAuth/CreateLogFiles.bash
cp /home/vagrant/httpd.conf.relevant /etc/apache2/sites-enabled/000-default
sudo chown -R www-data.www-data .
sudo chown vagrant.vagrant -R solr-4.7.2
sudo apachectl restart
cd MorrisDataDecorator
sudo chmod o+w *.out
bash run_all.bash
cd ../logs
sudo chmod o+w *.log
cd /home/vagrant/PriceHistory/solr-4.7.2/example
java -jar /home/vagrant/PriceHistory/solr-4.7.2/example/start.jar >& solroutput.log &

# Since we need a connection to SOLR, we want to give it time to get started up...
sleep 10

cd /home/vagrant/PriceHistory/PriceHistoryAPI
# do the loading
python SolrLodr.py
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/precise32"
  config.vm.provision :shell, :path => "bootstrap.sh"
  config.vm.provision "shell", inline: $buildStructures

  config.vm.provision :file do |file|
    file.source      = 'js.zip'
    file.destination = '/home/vagrant/js.zip'
  end

  config.vm.provision :file do |file|
    file.source      = 'cookedData.zip'
    file.destination = '/home/vagrant/cookedData.zip'
  end

  config.vm.provision :file do |file|
    file.source      = 'SlickGrid-master.zip'
    file.destination = '/home/vagrant/SlickGrid-master.zip'
  end

  config.vm.provision :file do |file|
    file.source      = 'solr-4.7.2.zip'
    file.destination = '/home/vagrant/solr-4.7.2.zip'
  end

  config.vm.provision :file do |file|
    file.source      = 'p3api.hashes.txt'
    file.destination = '/home/vagrant/p3api.hashes.txt'
  end

  config.vm.provision :file do |file|
    file.source      = 'p3api.passwords.txt'
    file.destination = '/home/vagrant/p3api.passwords.txt'
  end

  config.vm.provision :file do |file|
    file.source      = 'schema.PriceHistory.xml'
    file.destination = '/home/vagrant/schema.PriceHistory.xml'
  end

  config.vm.provision :file do |file|
    file.source      = 'httpd.conf.relevant'
    file.destination = '/home/vagrant/httpd.conf.relevant'
  end

  config.vm.provision "shell", inline: $copyFiles
  config.vm.network :forwarded_port, host: 4567, guest: 80
end
