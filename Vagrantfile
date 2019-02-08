# TODO: install agent plus copy over configuration

$script = <<SCRIPT
echo Starting provisioning...

apt-get update
apt-get install -y unzip

dpkg -i /vagrant/stackstate-agent_1.2.9-1_amd64.deb
ln -s /vagrant/stackstate.conf /etc/sts-agent/stackstate.conf

cd /opt/stackstate-agent/embedded
bin/pip install --upgrade pip
cd -

mv /etc/sts-agent/conf.d/disk.yaml.default /etc/sts-agent/conf.d/disk.yaml.example
mv /etc/sts-agent/conf.d/agent_metrics.yaml.default /etc/sts-agent/conf.d/agent_metrics.yaml.example
mv /etc/sts-agent/conf.d/network.yaml.default /etc/sts-agent/conf.d/network.yaml.example
mv /etc/sts-agent/conf.d/ntp.yaml.default /etc/sts-agent/conf.d/ntp.yaml.example

SCRIPT

Vagrant.configure("2") do |config|
#  config.vm.box = "ubuntu/trusty64"
  config.vm.box = "ubuntu/xenial64"
  config.vm.provision "shell", inline: $script
end
