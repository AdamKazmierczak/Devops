On our Storage server in Stratos Datacenter we are having some issues where nfsuser user is holding hundred of processes, which is degrading the performance of the server. Therefore, we have a requirement to limit its maximum processes. Please set its maximum process limits as below:

a. soft limit = 72
b. hard_limit = 98

Click on ✔ and Do Task Again
1>Update the file /etc/security/limits.conf with the below lines nfsuser soft nproc 72 nfsuser hard nproc 98 2>After saving the file run command as nfsuser so first run
su - nfsuser
3>Then check with below commands
ulimit -u -S ulimit -u -H
NOTE: THE values may change so update as per the requirement.
