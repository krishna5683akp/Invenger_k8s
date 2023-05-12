### Configuring schedule profiles
---------------------------------

* Before scheduling the prod we need to create a priority class. for that create a priorityclass object file in yaml.
* After writing the pod it will go through the ```Scheduling Queue``` ( ```PrioritySort Plugin``` ), Then it will go to the filter face ```Filtering``` (```NodeResourcesFit Plugin```,```NodeName```,```NodeUnschedulable``` Plugins)
The next phase is ```Scoring```(```NodeResourceFit```, ```ImageLocality``` Plugins) which node will score more then it will schedule on the that node by ```Binding``` (```DefaultBinder``` Plugin ) Face.

