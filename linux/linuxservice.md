## this needs to be 

# if you want to have this service working at startu run 
``
sudo systemctl enable nameofservice.service
``

## create file called nameofservice.service in folder 
## /etc/systemd/system/

# then create bash script which will run exact command as sudo / root

``
sudo cp /etc/kubernetes/admin.conf $HOME/
sudo chown $(id -u):$(id -g) $HOME/admin.conf
export KUBECONFIG=$HOME/admin.conf

# this is example command which connect to pod which runs a ceph-toolbox then it stops the ceph cluster
kubectl -n rook-ceph exec -it $(kubectl -n rook-ceph get pod -l "app=rook-ceph-tools" -o jsonpath='{.items[0].metadata.name}') ceph osd set noout
kubectl -n rook-ceph exec -it $(kubectl -n rook-ceph get pod -l "app=rook-ceph-tools" -o jsonpath='{.items[0].metadata.name}') ceph osd set nobackfill
kubectl -n rook-ceph exec -it $(kubectl -n rook-ceph get pod -l "app=rook-ceph-tools" -o jsonpath='{.items[0].metadata.name}') ceph osd set norecover
kubectl -n rook-ceph exec -it $(kubectl -n rook-ceph get pod -l "app=rook-ceph-tools" -o jsonpath='{.items[0].metadata.name}') ceph osd set norebalance
kubectl -n rook-ceph exec -it $(kubectl -n rook-ceph get pod -l "app=rook-ceph-tools" -o jsonpath='{.items[0].metadata.name}') ceph osd set nodown
kubectl -n rook-ceph exec -it $(kubectl -n rook-ceph get pod -l "app=rook-ceph-tools" -o jsonpath='{.items[0].metadata.name}') ceph osd set pause
``

# here is configuration needed for linux ubunt service which runs a script inside service as root (admin account = Ubuntu)

[Unit]
Description= Pause ceph cluster for maintenance /gracufull shutdown

[Service]
#Type=oneshot
User=ubuntu
#WorkingDirectory=/etc/systemd/system
#ExecStart=/bin/bash /home/ubuntu/pause.sh
ExecStart=/bin/bash /etc/systemd/system/pauseceph-pod.sh
#KillMode=process

[Install]
WantedBy=multi-user.target