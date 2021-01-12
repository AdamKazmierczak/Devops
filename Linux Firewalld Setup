https://www.youtube.com/watch?v=Jzk-V0UTdf4&feature=emb_logo


To secure our Nautilus infrastructure in Stratos Datacenter we have decided to install and configure firewalld on all app servers. We have Apache and Nginx services running on these apps. Nginx is running as a reverse proxy server for Apache. We might have more robust firewall settings in the future, but for now we have decided to go with the given requirements listed below:

a. Allow all incoming connections on Nginx port.
b. Allow incoming connections from LB host only on Apache port and block for all others.
c. All rules must be permanent.
d. Zone should be public.
e. If Apache or Nginx services aren't running already, please make sure to start them.


# do this on all app servers
#check your ports via grep command / nginx and apache
grep -i Listen /etc/httpd/conf/ht* /etc/nginx/nginx.conf

#install firewall
yum install firewalld -y

systemctl start firewalld && systemctl enable firewalld && systemctl status firewalld

#nginx add port 
firewall-cmd --zone=public --add-port=8093/tcp --permanent

firewall-cmd  --permanent --zone=public --add-service={http,https}

#add rules apachec + LB
firewall-cmd --permanent --zone=public --add-rich-rule='rule family="ipv4" source address="172.16.238.14" port protocol=tcp port=5002 accept'

#enable autostart of nginx 
systemctl enable nginx && systemctl status nginx 
#enable httpd autostart 
systemctl enable httpd && systemctl status httpd

systemctl restart nginx
systemctl status httpd

#important reload firewall settings after applying.be aware that this might stop your ssh conection and you might need to reconect again to stapp001--03
systemctl restart firewalld
#check rules
firewall-cmd --zone=public --list-all

#as a checkup do from any stapp and LB
#on stapp001-003
curl localhost:numberofapacheport
curl localhost:numberofnonaddedport
curl localhost:nginxport

#on LB
curl stapp001:apacheport
