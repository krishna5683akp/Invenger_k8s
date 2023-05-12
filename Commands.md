kubectl explain replicaset
kubectl replace <>
kubectl scale rs <name> replicas=4
kubectl edit rd <name>
kubectl run nginx --image=nginx
kubectl run nginx --image=nginx --dry-run=client -o yaml
kubectl create deployment --image=nginx nginx
kubectl create deployment --image=nginx nginx --dry-run=client -o yaml
kubectl create deployment --image=nginx nginx --dry-run=client -o yaml > nginx-deployment.yaml
kubectl create -f nginx-deployment.yaml
kubectl create deployment --image=nginx nginx --replicas=4 --dry-run=client -o yaml > nginx-deployment.yaml
kubectl get pods --namespace=<>
kubectl config set-context $(kubectl config current-context) --namespace= dev
kubectl get pods --all-namespace
kubectl expose deployment nginx --port 80
kubectl edit deployment nginx 
kubectl scale deployment nginx --replace=5
kubectl set image deployment nginx nginx=nginx:1.18

****** --dry-run=client. This will not create the resource, instead, 
			tell you whether the resource can be created and if your command is right.
-o yaml: This will output the resource definition in YAML format on screen
kubectl create deployment nginx --image=nginx --dry-run=client -o yaml > nginx-deployment.yaml
kubectl get pods --selectors app=app1 | wc(word count) -l
kubectl get pods --selectors app=app1 --no-headers | wc -l
** kubectl describe node kubemaster  | grep taint
kubectl label nodes <node-name> <label-key>=<label-value>
kubectl label node node01 size=Large
kubectl replace --force -f <file.yaml> (/tmp/kubectl-edit-33.yaml)
kubectl edit pod <pod name>
-------------------------------------

