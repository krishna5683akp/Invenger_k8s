### Encryption Secrets Data at Rest 
-------------------------------------

* First create a secrets using ```generic``` using --from-literal the command will look like ```kubectl create secret generic my-secret --from-literal=krishna=prasad``` 
* Now if i do ```kubectl get secret``` i will get to see my-secret.
* Now if i do ```kubectl describe secret my-secret``` i will get to see the secrets and data.
* Now if i do ```kubectl get secrets my-secret -o yaml``` i will see that my-secret defination file.
* Once i get the defination file i can see the encoded secret there. Then i can easily decode that value by using the following command ```echo -n "cHJhc2Fk" | base64 --decode```
* The command to install **etcdctl** ```apt-get install etcd-client```

 [link](https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/)

![Preview](./Images\Secrets1.png)

```
ETCDCTL_API=3 etcdctl \
   --cacert=/etc/kubernetes/pki/etcd/ca.crt   \
   --cert=/etc/kubernetes/pki/etcd/server.crt \
   --key=/etc/kubernetes/pki/etcd/server.key  \
   get /registry/secrets/default/<secret name> | hexdump -C
```   
* First we need to check encryption is enabled or not by following command ```ps -aux | grep kube-api | grep "--encryption-provider-config"```
* If you want to encrypt secret , use this command: ```head -c 32 /dev/urandom | base64```. This will generate a random key which can be used.
```yaml
---
apiVersion: apiserver.config.k8s.io/v1
kind: EncryptionConfiguration
resources:
  - resources:
      - secrets
    providers:
      - aescbc:
          keys:
            - name: key1
              secret: "cpoy the generated key here"
      - identity: {} 
```      

* Once you create the enc.yaml file you need to place that yaml file in the ```/etc/kubernetes/enc```
* Now you need to make changes in the kube-apiserver manifest file. 
* ```/etc/kubernetes/manifests/kube-apiserver.yaml``` now add the line ```--encryption-provider-config=/etc/kubernetes/enc/enc.yaml```
* After adding the line you need to volume and volume mounts.
* After encryption is enabled then only the newly created secrets can be encrypted. but if you want to encrypt the olders secrets you need to reploy those, this is the command to redeploy them ```kubectl get secrets --all-namespaces -o json | kubectl replace -f -```