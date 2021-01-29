ssh natasha@ststor01 

sudo su 
yum install -y nfs-utils nfs-utils-lib

vi /etc/exports
and add depending on theh description word for nfs mapping in this example it was nfsdata

#input here all app servers and proper right onto it.
/nfsdata 172.16.238.10(rw,sync,no_root_squash)
/nfsdata 172.16.238.11(rw,sync,no_root_squash)
/nfsdata 172.16.238.12(rw,sync,no_root_squash)

#enable service to auto start on ststor01
systemctl enable nfs-server && sudo systemctl start nfs-server && sudo systemctl status nfs-server

# go to the app servers and do the same thing on all app servers as bellow, via console or via ssh / you may need to instal openssh on storage server 
yum install openssh-clients openssh -y

#on storage server 
sudo su

#install nfs client packages 
systemctl enable nfs-server && sudo systemctl start nfs-server && sudo systemctl status nfs-server

#create requsted folder.
mkdir -p /var/www/nfsshare

#mount folder from storage server 
mount -t nfs ststor01:/nfsdata /var/www/nfsshare

#copy file 
sudo scp /tmp/index.html natasha@ststor01:/tmp
#then copy it on storage server to proper folder /shared
mv /tmp/index.html /nfsdata/

#check if you do see the mapped file
ls /nfsdata/

#you should see something like this 
[root@ststor01 natasha]# ls /nfsdata/
index.html

