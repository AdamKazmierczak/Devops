## ssh to stapp01 

#logon as sudo 
```
sudo su -
```
# check if service regarding nfs server is running

systemctl status nfs-server
systemctl start nfs-server

# it does not rung aparently so let's check configuration
```
sudo vi /etc/exports
```

# there is some misconfiguration regarding ip so let's change those. Configuration regarding etc/export should have only ip and setup off acces to the share

# such as bellow
# /nameofshare ip_of_app_server001 (acces type) bellow example

/webdata 172.16.238.11 (rw,sync,no_subtree_check,no_root_squash,fsid=0)  # this needs to be repeated 3 times due to 3 app servers exist

# then restart nfs server service 

```
systemctl restart nfs-server

# check shares via exportfs command -a all directory , -v verbose
exportfs -av 

# go to stapp01 and mount share and check if it works.

```
ssh tony@stapp01
sudo su -
systemctl start nfs-server
systemctl start nfs-server
```
# check mount status
showmount -e ststor01

# mount folder
```
mount -t nfs ststor01:/webdata /var/www/html
df -h 

# as final test you may create a file inside /var/www/html and check if it is visible on stapp02. On stapp02 you would need also add mount folder 
