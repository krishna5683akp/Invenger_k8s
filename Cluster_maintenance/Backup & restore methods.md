* If you want to take the backup of the ETCD cluster run the following command 
```ETCDCTL_API=3 etcdctl  \ snapshot save snapshot.db```
* After that stop the API server ```service kube-apiserver stop```   
* ```ETCDCTL_API=3 etcdctl  \ snapshot restore snapshot.db \ --data-dir /var/lib/etcd-from-backup```
* Then daemon reload ```systemctl daemon-reload```
* Then ```service etcd restart```
* Then ```service kube-apiserver start```
* For example, if you want to take a snapshot of etcd, use:
    ```etcdctl snapshot save -h``` and keep a note of the mandatory global options

* Since our ETCD database is TLS-Enabled, the following options are mandatory:

   ```--cacert```     verify certificates of TLS-enabled secure servers using this CA bundle

    ```--cert```   identify secure client using this TLS certificate file

    ```--endpoints=[127.0.0.1:2379]``` This is the default as ETCD is running on master node and exposed on localhost 2379.

    ```--key``` identify secure client using this TLS key file

* 
