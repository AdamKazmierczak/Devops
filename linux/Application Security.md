We have a backup management application UI hosted on Nautilus's backup server in Stratos DC. That backup management application code is deployed under Apache on the backup 
server itself, and Nginx is running as a reverse proxy on the same server. Apache and Nginx ports are 6100 and 8094, respectively. 
We have iptables firewall installed on this server. Make the appropriate changes to fulfill the requirements mentioned below:
We want to open all incoming connections to Nginx's port and block all incoming connections to Apache's port. Also make sure rules are permanent.

Click on ✔ and Do Task Again
# to open all incoming connections to Nginx's port / accept any new and established connections
sudo iptables -A INPUT -p tcp --dport 8096 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT 

# to block all incoming connections to Apache's port /reject any new connections
sudo iptables -A INPUT -p tcp --dport 6100 -m conntrack --ctstate NEW -j REJECT 

# check out rules
sudo iptables -L

# iptables-save  ##to save it permanently. 
# you will be able to see the rules in the files /etc/sysconfig/iptables
sudo service iptables save

# if you do check out via cat

cat /etc/sysconfig/iptables

# you should see something like this 
-A INPUT -p tcp -m tcp --dport 8096 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -m tcp --dport 6100 -m conntrack --ctstate NEW -j REJECT --reject-with icmp-port-unreachable



