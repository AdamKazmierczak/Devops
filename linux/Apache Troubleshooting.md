xFusionCorp Industries utilizes monitoring tools to check the status of every service, application, etc. running on the systems. The monitoring system identified that Apache service is not running on some of the Nautilus Application Servers in Stratos Datacenter.
Identify the faulty Nautilus Application Servers and fix the issue. Also, make sure Apache service is up and running on all Nautilus Application Servers. Do not try to stop any kind of firewall that is already running.
Apache is running on 8084 port on all Nautilus Application Servers and its document root must be /var/www/html on all app servers.
Finally you can test from jump host using curl command to access Apache on all app servers and it should work fine. E.g. curl http://172.16.238.10:8084/

Click on ✔ and Do Task Again
Ssh to all app servers 

#ssh to stapp01
stapp01 
sudo vi /etc/httpd/conf/httpd.conf

#edit to proper value
ServerRoot "etc/httpd"
Listen 172.16.238.10:8084

#then restart httpd service
sudo systemctl start httpd
sudo systemctl status httpd

#curl for check up stapp01
curl http://172.16.238.10:8084

#then ssh to stapp02

sudo systemctl start httpd
sudo systemctl status httpd.service

sudo vi /etc/httpd/conf/httpd.conf

#edit to proper value
ServerRoot "etc/httpd"

#start httpd /apache service
sudo systemctl start httpd
sudo systemctl status httpd.service

#check to reasure
curl 172.16.238.11:8084

#ssh to stapp03
#check configuration of httpd.conf
sudo vi /etc/httpd/conf/httpd.conf
#change configuration of Listen value to proper 8084
Listen 172.16.238.10:8084

#start httpd /apache service
sudo systemctl start httpd
sudo systemctl status httpd.service

#check to reasure
curl 172.16.238.12:8084
