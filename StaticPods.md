### Static Pods

* Kubelet on Node can manage Node Independently.
* Static pod path: ```/etc/kubernetes/manifests```
* If there is no any manifest files go the ```/var/lib/kubelet/config.yaml``` there you can find the Static Pod path. 
* static pod path in kubeletc.service file is --config= kubeconfig.yaml
* Check above those paths before inspecting the existing cluster if require.


  | Static Pods | Daemonsets |
  | ------------|------------|
  | Created by kubelet | Created by KUBE_API Sever (Daemonsets Controller) |
  | Deploy Control plane components as Static Pods | Deploy Monitoring agents, Logging agents on nodes |
* Both are ignored by the scheduler.