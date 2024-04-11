* ```apt-get upgrade -y kubeadm=<version>``` to update the kubeadm
* ```kubeadm upgrade apply <version>``` it will upgrade
* if you want to upgrade the kubelet version in nodes folloe this commands
    * first drain your worker nodes  ```kubectl drain <node name>```
    * ```apt-get upgrade -y kubeadm=<version>```
    * ```apt-get upgrade -y kubelet=<version>```
    * ```kubeadm upgrade node config --kubelet-version=<version> ```
    * ```systemctl restart kubelet```
