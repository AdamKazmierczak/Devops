There are specific access levels for users defined by the xFusionCorp Industries system admin team. Rather than providing access levels to every individual user, the team has decided to create groups with required access levels and add users to that groups as needed. See the following requirements:
a. Create a group named nautilus_developers in all App servers in Stratos Datacenter.
b. Add the user kano to nautilus_developers in all App servers. (create the user if not present already)

Click on ✔ and Do Task Again
#all is needed here is to ssh to all app servers 
ssh tony@stapp01
ssh steve@stapp02
ssh banner@stapp03
#then run as sudo command to add user to nautilis_developers group where kano means user name. This command will add  user.
sudo usermod –aG nautilus_developers kano
