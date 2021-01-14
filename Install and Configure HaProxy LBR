sudo yum update 
sudo yum install haproxy 

#ssh to all app servers and check on which port they are listeing http 
 cat /etc/httpd/conf/httpd.conf |grep Listen
 
 #you  should see something like this 
 
 # Listen: Allows you to bind Apache to specific IP addresses and/or
# Change this to Listen on specific IP addresses as shown below to
#Listen 12.34.56.78:80
Listen 6200
[steve@stapp02 ~]$ curl stapp02:6200

#then edit haproxy via 
sudo nano /etc/haproxy/haproxy.cfg

#Change default port of haproxy 5000 to 80
#it should look like something like that 
#---------------------------------------------------------------------
frontend main
    bind *:80 

#add parameters regarding other app server / at the end of file change default settings.
server stapp01 172.16.238.10:6200 check                 
server stapp02 172.16.238.11:6200 check 
server stapp03 172.16.238.12:6200 check 

#restart haproxy 
sudo systemctl restart haproxy

#curl haproxy Loadbalancer server/ you should be redirected to Welcome to xFusionCorp Industries !
curl stlb01:80  / repeat 3 times to check roundrobin.

or use the + to check out webpage. 
