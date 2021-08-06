## in this task you need to save image from local repo to tar format and copy it to another server the load it into repository

## first initial command , you may need to logon via ssh to stap001 and then run commands as sudo

## to check images
sudo docker images

## save images to folder location in this example we are going with temp folder
## where tmp/blog.tar is location of docker file
## blog:devops is image name and tag 

sudo docker save -o /tmp/blog.tar blog:devops

## copy file from stap01 to example stapp03 via scp command 

cd /tmp/

scp /tmp/blog.tar banner@stapp03:/tmp

## then you need go to another server via ssh username@stapp03 

## check docker service status / run it 

sudo systemctl status docker
sudo systemctl start docker

## load image into repo from location you 
cd /tmp

docker load -i blog.tar

## and that's all :)
