* If the node was down for 5 min, then the pods are terminated from that node. k8s consider them as dead.
* If the pods were part of the replicaset, then they are recreated on the other nodes.
* The time it waits for a pod to come back online is known as the **Pod-eviction-timeout** and is set on the k8s control manager with default values of 5min.
* So while doing maintenance we are not sure about the time, how long the node is down and when it comes. 
* There is a safer  way to do this. You can purposefully drain the node of all the workloads so that the workloads are moved. the command to drain the node ```kubectl drain <node name>```. Then the node is also cordoned or marked as unschedulable. pods on the node are gracefully terminates then it will place on other nodes.
* Once the node came back to online you have to do uncordon ```kubectl uncordon <node name>``` so the pods can be scheduled on it again.
* There is another command called ```kubectl cordon <node name>```. It will not terminate the pods from the node but it will mark the node as unschedulable.

