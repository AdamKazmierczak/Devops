#install authentication method for apache 
yum --enablerepo=epel -y install mod_authnz_external pwauthv

#go to authnz file and add content regarding type of authenticatin for PAM 
vi /etc/httpd/conf.d/authnz_external.conf

#add info
<Directory /var/www/html/protected>
AuthType Basic
Authname "PAM Authentication"
AuthBasicProvider external
AuthExternal pwauth
require valid-user
</Directory>

#create shared protected folder
mkdir -p /var/www/html/protected

#check if everything is ok
cat /var/www/html/protected/index.html

#check startup httpd apache
systemctl status httpd && systemctl start httpd

#check if you can acces protected folder 
curl -u kirsty:B4zNgHA7Ya http://localhost/8080/protected

logon to loadbalancer and go to + and choose port 80 / you should not see content
