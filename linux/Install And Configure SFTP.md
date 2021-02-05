# ssh to app server in this example app01
ssh tony@stapp01

# sudo su - / as root
sudo su -

# check if user from taks is created  in this example javed
id javed 

# if it is not created , then create it 

useradd javed 

# add password 
 passwd javed
 
 # make folder for sftp in this example code in required folder
   mkdir /var/www/code
  
# check configuration of sshd_config / daemon  and grep config for sftp

cat /etc/ssh/sshd_config |grep sftp -A 10

# you should see something like this which is missing some configuration required for task.

Subsystem       sftp    /usr/libexec/openssh/sftp-server

# Example of overriding settings on a per-user basis

-#Match User anoncvs
-#       X11Forwarding no
-#       AllowTcpForwarding no
-#       PermitTTY no
-#       ForceCommand cvs server


# to have fully it configured you need to edit file and add configuration as bellow.

subsystem sftp internal-sftp 
Match User javed
ForceCommand internal-sftp
PasswordAuthentication yes
ChrootDirectory  /var/www/code  # this is just an example /check your task folder
PermitTunnel no
AllowAgentForwarding no
AllowTcpForwarding no
X11Forwarding no

# Example of overriding settings on a per-user basis

#Match User anoncvs
-#       X11Forwarding no
-#       AllowTcpForwarding no
-#       PermitTTY no
-#       ForceCommand cvs server


#  add proper permission to folder created

chown root:root /var/www     # add ownership to folder

chmod -R 755 /var/www        # add permissions

chmod -R 755 /var/www/code   # add permissions

chown -R javed /var/www/code # add ownership to folder

chown -R root /var/www/code  # add ownership

chown -R root /var/www/      # add ownership to folder

# restart systemctl deamon to adjust changes

systemctl restart sshd

# check user acces and input password

sftp javer@localhost # should be granted

ssh javer@localhost # should not be granted
