The Nautilus system admins team recently deployed a web UI application for their backup utility running on the Nautilus backup server in Stratos Datacenter. The application is running on port 3001. They have firewalld installed on that server. The requirements that have come up include the following:
Open all incoming connection on 3001/tcp port. Zone should be public.

Click on ✔ and Do Task Again
firewall-cmd --zone=public --add-port=3001/tcp --permanent
firewall-cmd --reload
