#it's quite easy task just to find and identify proces which stops apache from starting. problematic server is stapp01 but check also other servers.

# Go to ssh steve@stapp01
#then check status of httpd
sudo systemctl status httpd
sudo systemctl start httpd
sudo systemctl status httpd 
#you should see here that process is blocked by another one
#double check if the  apache is listening on the same port by using command
cat /etc/httpd/conf/httpd.conf |grep Listen 

#check proces of service running in netstat it should be the same as it is in logs of systemctl status httpd
netstat -tulnp

#check it via show process in granular approach (grep 321) where 321 is example proces PID
ps -ef | grep 321

#kill the process via kill command 
kill -9 321

#run httpd 
sudo systemctl start httpd 

#check other stapp servers via ssh and systemctl status httpd 
