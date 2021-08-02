## in this task you are requested to do download docker image and change it's tag. To do so 

## use command as bellow.
docker pull busybox:sometag

## tag a docker image via image id

docker tag 0e5574283393 fedora/httpd:version1.0

## Tag an image referenced by Name and Tag
## To tag a local image with name “httpd” and tag “test” into the “fedora” repository with “version1.0.test”:

docker tag httpd:test fedora/httpd:version1.0.test

## then remove old image with old tag

docker image rm nameofdockerimage:tagname

## example 

docker imager rm busybox:sometag
