### Rolling updates and Rolling back 
------------------------------------

* Rollout command ```kubectl rollout status deployment/myapp-deployment```
* Rollout history ```kubectl rollout history deployment/myapp-deployment```
* Rolling update is the default deployment strategy. 
* Recreate is also one of the deployment strategy but there is down time for the application, But if you use the Rolling update there will no downtime for the application.
* If you want to Rollout use the following command ```kubectl rollout undo deployment/myapp-deployment```