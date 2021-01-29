The production support team of xFusionCorp Industries is working on developing some bash scripts to automate different day to day tasks. One is to create a bash script for taking websites backup. They have a static website running on App Server 3 in Stratos Datacenter, and they need to create a bash script named beta_backup.sh which should accomplish the following tasks. (Also remember to place the script under /scripts directory on App Server 3)
a. Create a zip archive named xfusioncorp_beta.zip of /var/www/html/beta directory.
b. Save the archive in /backup/ on App Server 3. This is a temporary storage, as backups from this location will be clean on weekly basis. Therefore, we also need to save this backup archive on Nautilus Backup Server.
c. Copy the created archive to Nautilus Backup Server server in /backup/ location.
d. Please make sure script won't ask for password while copying the archive file. Additionally, the respective server user (for example, tony in case of App Server 1) must be able to run it.

Click on ✔ and Do Task Again
#ssh to stapp02

sudo vi /scripts/media_backup.sh

zip -r /backup/xfusioncorp_media.zip /var/www/html/media
scp /backup/xfusioncorp_media.zip clint@stbkp01:/backup/

#generate backup ssh-keys
ssh-keygen

#input password for Clint
ssh-copy-id clint@stbkp01

#as for checkup
bash  scripts/media_backup.sh
