* Daemonsets will maintain the a pod in every nod.
* If the new node is added one pod will allocate on the node and if the node is deleted the pod will also deleted.
* The main purpose of the Daemonsets for ```Monitoring Solution, Logs viewer```
* In this case we can deploy monitoring agent in the form of pod in all our nodes in the cluster.
* We dont need to add or remove pod in this case. Daemonsets will take care for us.
* Some basic Commands ```kubectl apply -f daemonsets.yaml, kubectl get daemonsets, kubectl describe daemonsets <name>```
### How does Daemonsets works?
* If we want to create a every pod to schedule on each node we need to use the NodeProperty in Pod section.
this is before k8s V1.12.
* After V1.12 k8s uses Nodeaffinity and default scheduler to schedule the each pod on the each node.
* ```kubectl describe daemonsets <name> -n <namespace>,``` 
* To test some creation without executing use and we can give that output some yaml file. ```--dry-run=client -o yaml > something.yaml``` 
