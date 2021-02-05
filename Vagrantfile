# TODO: install agent plus copy over configuration

$script = <<SCRIPT
echo Starting provisioning...

apt-get update
apt-get install -y unzip

curl -o- https://stackstate-agent-2.s3.amazonaws.com/install.sh | \
    STS_API_KEY="f23e5a0a-ad83-4710-9037-1879fee26edc" \
    STS_URL="http://localhost/stsAgent" bash

ln -s /vagrant/stackstate.conf /etc/stackstate-agent/stackstate.conf

SCRIPT

Vagrant.configure("2") do |config|
#  config.vm.box = "ubuntu/trusty64"
  config.vm.box = "ubuntu/xenial64"
  config.vm.provision "shell", inline: $script
end
