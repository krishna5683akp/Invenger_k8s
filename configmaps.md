### ConfigMaps ans Secrets configuration
------------------------------------------

* There are two phases involved in configuring ConfigMaps
    * Create the ConfigMap.
    * Inject them into Pod.
* There are two ways of configuring ConfigMaps 
    * Imperative way 
    * The Declarative way by creating a ConfigMaps.yaml
------------------------------------------------------------
### Secrets Configuration

* There are two phases involved in configuring Secrets
    * Create the Secrets.
    * Inject them into Pod.
* There are two ways of configuring Secrets 
    * Imperative way 
    * The Declarative way by creating a Secrets.yaml
* In this case secrets defination file we need to store our values in encoded format.
* How to encode the values in encoded format use the ```base64``` online converter or use the linux host ```echo -n 'password' | base64```.
* If you want to decode the values that you have encoded use base64 decode like ```echo -n 'cGFzc3dvcmQ=' | base64 --decode``` or else use the online base64 decode converter.
### Note:    
    * While using the secrets we need to remember onething secrets are not encrcypted. Only encoded. meaning anyone can look up the secrets defination file and they can decode the values as we mentioned above. As such the secrets can be considered as not very safe.
    * Do not push the Secrets objects into SCM along with code.
    * Secrets are not encrypted in ETCD.
        * Enable encryption at rest.
    * Anyone able to create the Pod/Deployments in the same namespace can access the sercets.
        * Configure least privilage access to user- RBAC
    * Consider third-party secret store providers
        AWS provider, AZURE provider, GCP provider, VAULT provider.


