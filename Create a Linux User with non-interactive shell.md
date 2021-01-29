Task Details
The System admin team of xFusionCorp Industries has installed a backup agent tool on all app servers. As per the tool's requirements they need to create a user with a non-interactive shell.
Therefore, create a user named rose with a non-interactive shell in the app03 server

Click on ✔ and Do Task Again
#ssh to app server 03

#the run command 
sudo useradd rose -s /sbin/nologin
#where -s /sbin/nologin will create the noninteractive user account.
#rose stand for username.
