### Encryption Secrets Data at Rest 
-------------------------------------

* First create a secrets using ```generic``` using --from-literal the command will look like ```kubectl create secret generic my-secret --from-literal=krishna=prasad``` 
* Now if i do ```kubectl get secret``` i will get to see my-secret.
* Now if i do ```kubectl describe secret my-secret``` i will get to see the secrets and data.
* Now if i do ```kubectl get secrets my-secret -o yaml``` i will see that my-secret defination file.
* Once i get the defination file i can see the encoded secret there. Then i can easily decode that value by using the following command ```echo -n "cHJhc2Fk" | base64 --decode```
* [link] (https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/).

![Preview] (./Images\Secrets1.png)