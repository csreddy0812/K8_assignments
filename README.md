What are the differences file-wise?
Differences:
Kind : ReplicationController & ReplicaSet
matchLabels added for kubia-replicaset 
 containerPort: 8080 added for kubia-rc
 
 
[root@ip-172-31-28-137 05-services]# kubectl apply -f kubia-replicaset.yaml
replicaset.apps/kubia created
[root@ip-172-31-28-137 05-services]# kubectl get pods
NAME          READY   STATUS              RESTARTS   AGE
kubia-bh9z2   1/1     Running             0          9s
kubia-gd6vh   0/1     ContainerCreating   0          9s
kubia-gq7bc   1/1     Running             0          9s
[root@ip-172-31-28-137 05-services]# kubectl get pods
NAME          READY   STATUS    RESTARTS   AGE
kubia-bh9z2   1/1     Running   0          15s
kubia-gd6vh   1/1     Running   0          15
