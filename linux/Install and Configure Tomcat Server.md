## ssh to proper app server

## install tomcat
sudo su 
yum install tomcat -y

# apply port changes on tomcat server 
vi /usr/share/tomcat/conf/server.xml 

find text with text such as port 8080 and change port number like on example bellow

[root@stapp02 steve]# cat /usr/share/tomcat/conf/server.xml |grep port
<Server port="8005" shutdown="SHUTDOWN">
         Define a non-SSL HTTP/1.1 Connector on port 8080
    <Connector port="8080" protocol="HTTP/1.1"    ---- change here port 8080 to port from your task
               port="8080" protocol="HTTP/1.1"    ---- change here port 8080 to port from your task
    <!-- Define a SSL HTTP/1.1 Connector on port 8443
    <Connector port="8443" protocol="org.apache.coyote.http11.Http11Protocol"
    <!-- Define an AJP 1.3 Connector on port 8009 -->
    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />
    <!-- You should set jvmRoute to support load-balancing via AJP ie :

# check port changes on tomcat server
cat /usr/share/tomcat/conf/server.xml |grep port

#  you shoul see something like this 

<Server port="8005" shutdown="SHUTDOWN">
         Define a non-SSL HTTP/1.1 Connector on port 8080
    <Connector port="8080" protocol="HTTP/1.1"   
               port="8080" protocol="HTTP/1.1"    
    <!-- Define a SSL HTTP/1.1 Connector on port 8443
    <Connector port="8443" protocol="org.apache.coyote.http11.Http11Protocol"
    <!-- Define an AJP 1.3 Connector on port 8009 -->
    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />
    <!-- You should set jvmRoute to support load-balancing via AJP ie :
    
# start tomcat server / it is not running by default
systemctl start tomcat

# check if it is running 
systemctl status tomcat
    
# check if file is visible via curl and proper port / bear in mind that ip might change due to app server from your task
curl -i 172.16.238.12:8083
