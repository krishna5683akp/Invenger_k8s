### k8s cluster upgrade process

* In k8s cluster none of the other component than kube api server should not have higher version they should be lower than api-server
* example api-server v1.10
    * control manager v1.10 or v1.09
    * kube-scheduler v1.10 or v1.09
    * kubelet v1.10 or v1.09 or v1.08
    * kube-proxy v1.10 or v1.09 or v1.08
* if it is kubeadm 
    * kubeadm upgrade plan
    * kubeadm upgrade apply
* If it is managed by cloud platforms it is easy to upgrade by clicking some options
* If it is from scratch it hard to upgrade but we can
* First we need to upgrade the master node then upgrade the worker nodes.
* If we upgrade the master still users can acces the application but the thing is we can't deploy any new application using kubectl because the master component is upgrading.
* There are different strategies to upgrade the worker nodes
    * upgrade all of them at once
        * Then our pods all will be down and the users can not access the applicatoon.
    * Upgrade one at a time
    * Nodes with newer version 
        * add the new version nodes to the cluster then moov the workloads from the old nodes to new nodes

### Kubeadm Upgrade

* ```kubeadm upgrade plan```
* It will give the better out put like cluster version and all
* After we upgrade the master plane components we need to upgrade the kubelet versions manually on each node
kubeadm does not install or upgrade kubelets.
```
apt-get upgrade -y kubeadm=1.12.0-00
kubeadm upgrade apply v1.12.0
```
```
apt-get upgrade kubelet=1.12.0-00
systemctl restart kubelet
kubectl get nodes
```

* To update the worker node first we need to moov the workload from that node for that we need to us the command ```kubelet drain node-1``` its also cordon the node and marks it like unschedulable, so no new pods will schedule on it.
```apt-get upgrade -y kubeadm=1.12.0-00
apt-get upgrade -y kubelet=1.12.0-00
kubeadm upgrade node config --kubelet-version v1.12.0
systemctl restart kubelet
```
* while upgrading the node to newversion we marked it as unschedulable, so we need to uncordon it again
```kubectl uncordon node-1```
* Perform this in every worker node to upgrade the worker nodes.

