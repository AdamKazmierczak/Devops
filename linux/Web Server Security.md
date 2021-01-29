Click on ✔ and Do Task Again

curl -I http://172.16.238.12:8080

sudo systemctl status httpd

sudo systemctl start httpd

sudo systemctl status httpd

Added below 2 lines end of config file : /etc/httpd/conf/httpd.conf

ServerTokens Prod
ServerSignature Off

Modified below details in config file :slight_smile:

<Directory “/var/www/html”>
Options -Indexes +FollowSymLinks
AllowOverride None
Require all granted
sudo systemctl restart httpd

Its worked for me

Validate the apache version not exposed
curl -I http://IP_address:8080
