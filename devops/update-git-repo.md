
scp index.html  natasha@ststor01:/temp

ssh natasha@ststor01

cp /tmp/index.html /usr/src/kodekloudrepos/news  #name of repo news

cd /usr/src/kodekloudrepos/news

## as sudo 
git add .
git commit -m "anny text here"
git push 

## end 