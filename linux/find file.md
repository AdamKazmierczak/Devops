Click on ✔ and Do Task Again

#There are 2 methods do this task
#i would go with the yum -y install mlocate

#then find files with extension js via 
mlocate /var/www/html/ecommerce/*.js


after that use command 
` find /var/www/html/official -type f -name '*.css' -exec cp --parents {} /official \;