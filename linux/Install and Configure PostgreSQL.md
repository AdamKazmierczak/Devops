Install postgresql:
------------------                                        
yum install postgresql-server postgresql-contrib  -y

setup postgresql:
----------------                                
postgresql-setup initdb    

enable, start &  check service postgresql:
-----------------------------------------                                        
systemctl enable postgresql && sudo systemctl start postgresql                        
systemctl status postgresql            

Enter into postgresql database:
------------------------------                                    
sudo -u postgres psql postgres        

Create user, database, and grant permission:
--------------------------------------------                        
CREATE USER kodekloud_sam WITH PASSWORD 'YchZHRcLkL';                    
CREATE DATABASE kodekloud_db2;                                    
GRANT ALL PRIVILEGES ON DATABASE "kodekloud_db2" to kodekloud_sam;    


Set the config for local:
------------------------                                            
sudo vi /var/lib/pgsql/data/pg_hba.conf    

local all all md5                                                
host all all 127.0.0.1/32 md5 

Next open another config:            
------------------------                            
sudo vi /var/lib/pgsql/data/postgresql.conf                                    
Uncomment listen_address=localhost        

save &  exit

restart    service & check status:
--------------------------------                                                
sudo systemctl restart postgresql                                        
sudo systemctl status postgresql.service    


Finally Check:
-----------                                    
psql -U kodekloud_sam -d kodekloud_db2 -h 127.0.0.1 -W                            
psql -U kodekloud_sam -d kodekloud_db2 -h localhost -W     
