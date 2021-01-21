#first on jump server identify which app server is not responsive  /remember port 5000 is example
telnet stapp01 5000
telnet stapp02 5000
telnet stapp03 5000

#ssh to problematic server
#check httpd /apache server
sudo systemclt status httpd

#start httpd 
sudo systemclt start httpd

#check logs / it looks like service can't start because something is working under apache pid 
#check which service is working under the same pid 
netstat -tulnp
#identify service and kill it. in this example Pid number is 404
sudo ps -ef |grep 404
sudo kill 404

#start apache server and check logs again 
sudo systemctl start httpd

#go to apache server configuration file and check the server name 
vi /etc/httpd/conf/httpd.conf

#add missing server name which is commented such as 
ServerName ipofproblematicappserver 5000 
#save and quit 

#restart again httpd
sudo systemctl restart httpd

#check telnet on jump server
Telnet stapp01 5000

#last thing here is iptables which seems to be blocking even with proper rules 
#flush the iptables and try again with Telnet.
iptables -F 
