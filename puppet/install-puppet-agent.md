
## add puppet repository depending on your centos os version add 7 or 8 in link below
## to check centos os version use 
hostnamectl

sudo rpm -Uvh https://yum.puppet.com/puppet7-release-el-7.noarch.rpm

#install puppet 
sudo yum install puppet-agent -y

##start puppet service
service puppet start

##check puppet service statsu
systemctl status puppet