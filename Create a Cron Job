#ssh to every app server with aproriate user 
#install cronie on app servers  where 
#cronie stand for cron package 
#-y is for automatic confirmation

Click on ✔ and Do Task Again
yum install cronie -y  
sudo systemctl start crond.service
sudo systemctl status crond.servic

# to change cron run job  for root 

sudo crontab -e

# input here as requested  */5 * * * * echo hello > /tmp/cron_text 
#save file :w and quit :q

#list jobs per user in your case root
 crontab -u <username> -l
  crontab -u root -l
#
#Field	Allowed Values
#minute	0-59
#hour	0-23
#Day of the month	1-31
#month	1-12 or JAN-DEC
#Day of the week	0-6 or SUN-SAT
#Together, tasks scheduled in a crontab are structured like this:

#example definition
minute hour day_of_month month day_of_week command_to_run

#list jobs per user 
 crontab -u <username> -l
