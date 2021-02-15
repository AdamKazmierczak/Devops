Creating directory is simple
Adding user:
# add user with password
htpasswd -c /etc/httpd/.htpasswd username

# restart https service 
sudo systemctl restart httpd && sudo vi /etc/httpd/conf/httpd.conf

Create basic .htaccess file
first create folder 
mkdir /var/www/html/itadmin

# create config file for folder acces
cd /var/www/html/itadmin/
/var/www/html/itadmin/.htaccess <----------- itadmin is the new directory created

# or
sudo vi /var/www/html/itadmin/.htaccess
# add configuration as bellow.

AuthType Basic
AuthName “Restricted Content”
AuthUserFile /etc/httpd/.htpasswd
Require valid-user

# check if configuration regarding appache is compliant.
sudo vi /etc/httpd/conf/httpd.conf

<Directory “/var/www/html/itadmin”> <--------- itadmin is the new directory name
AllowOverride AuthConfig

# opy index.html file in new terminal window / jump server

Scp /tmp/index.html file from jumpbox to app server (/var/www/html/itadmin/index.html).
scp /tmp/index.html tony@stapp01:/tmp

#again on stapp01 copy index.html to proper folder
sudo cp /tmp/index.html /var/www/html/itadmin

# Restart httpd service
sudo systemctl restart httpd

# Test connectivity first with user
curl -u yousuf:GyQkFRVNr3 http://stapp01:8080/itadmin/
where yousuf is the new user created followed by password

# then doublecheck without user input
curl  http://stapp01:8080/itadmin/
