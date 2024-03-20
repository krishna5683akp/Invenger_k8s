### Backups and Restore

### Backup Candidates

* Here we know that everything related to the cluster information that will be stored in the ```ETCD```
* if our apllication is configured with the persistant storage ```Persistant Volume``` we need to take the back up these two things.
* A good way is to store all the application related defination files in the ```GitHub``` so we can maintain the history.
* ```kubectl get all --all-namespace -o yaml > all.deploy.service.yaml```

### Backup ETCD

* while configuring the etcd we specified a dir where all the data would be stored for ex: ```--data-dir= /var/lib/etcd```
* This is the directory that can be backed up by our backup tool like "verelio"
* etcd also comes with built in snapshot solution. you can take the snapshot of etcd db by using the etcd controll utilities snapshot save command.
```
ETCDCTL_API=3 etcdctl \
    snapshot save snapshot.db
ls
ETCDCTL_API=3 etcdctl \
    snapshot status snapshot.db
```
* To restore the cluster form the backup at later point in time 
    * First stop the kube-apiserver service
        * service kube-apiserver stop
    * Then run the etcd controls snapshot restore command with the path set to the backup
        ```
        ETCDCTL_API=3 etcdctl \
            snapshot restore snapshot.db \
            --data-dir /var/lib/etcd-from-backup
        systemctl daemon-reload
        service etcd restart
        service kube-apiserver start
        ```
* But if it is a managed k8s service backup by quering the kube-apiserver is the better way.
* Since our ETCD database is TLS-Enabled, the following options are mandatory:
```
--cacert  verify certificates of TLS-enabled secure servers using this CA bundle
--cert  identify secure client using this TLS certificate file
--endpoints=[127.0.0.1:2379]  This is the default as ETCD is running on master node and exposed on localhost 2379.
--key  identify secure client using this TLS key file
```

* Similarly use the help option for snapshot restore to see all available options for restoring the backup.

* ```etcdctl snapshot restore -h```
