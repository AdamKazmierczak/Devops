```

yum install iptables-services -y

systemctl status iptables
systemctl start iptables
systemctl enable iptables
iptables -L
iptables -A INPUT -p tcp --destination-port 8088 -s 172.16.238.14 ACCEPT 
Iptables _a INPUT -p tcp --desitnation-port 8088 -j DROP

service iptables save 
systemctl restart iptables 
```

# in some cases you would need to reset iptables and redo adding rules 
#to do so 
```
iptables -F
```
# to list iptables.
```
iptables -S 
```
# and do the same thing as bellow

```
iptables -A INPUT -p tcp --destination-port 8088 -s 172.16.238.14 ACCEPT 
Iptables _a INPUT -p tcp --desitnation-port 8088 -j DROP
service iptables save 
systemctl restart iptables 

from loadbalancer
curl -I stapp01:8088
```
