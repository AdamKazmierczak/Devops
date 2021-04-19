# at some cases environment for python do not work that's why first you need to install ansible via package manager then downgrade it via pip
## install ansible via package manager
sudo yum -y install ansible

## downgrade it via pip / python.
pip install ansible==2.5.7
