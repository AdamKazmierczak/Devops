Click on ✔ and Do Task Again
sudo vi /etc/ssh/sshd_config

#uncomment PermitRootLogin yes and change it to 
PermitRootLogin no
#then write changes :w and quit :q
#run restart of SSH daemon 
sudo systemctl restart sshd
