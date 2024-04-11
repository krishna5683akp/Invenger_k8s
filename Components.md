* API Server (APIServer):
    * kube-apiserver
    * Description: Exposes the Kubernetes API and serves as the front-end for the Kubernetes control plane.
* Scheduler:
    * kube-scheduler
    * Description: Assigns newly created pods to nodes based on resource availability and constraints.
* Controller Manager:
    * kube-controller-manager
    * Description: Runs controller processes that regulate the state of the cluster, such as node and replication controllers.
* Kubelet:
    * Description: An agent that runs on each node and ensures that containers are running in a pod as expected.
* Kube-proxy:
    * Description: Maintains network rules on nodes, implementing Kubernetes Service abstraction.
* etcd:
    * Description: Consistent and highly available key-value store used as Kubernetes' backing store for all cluster data.
* Container Runtime:
    * Description: The software responsible for running containers, such as Docker, containerd, or CRI-O.