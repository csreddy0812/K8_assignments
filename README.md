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



[root@ip-172-31-28-137 05-services]# kubectl apply -f kubia-svc.yaml
service/kubia created
[root@ip-172-31-28-137 05-services]# kubectl get svc
NAME         TYPE        CLUSTER-IP    EXTERNAL-IP   PORT(S)   AGE
kubernetes   ClusterIP   10.96.0.1     <none>        443/TCP   39h
kubia        ClusterIP   10.99.10.99   <none>        80/TCP    5s

[root@ip-172-31-28-137 05-services]# curl -k http://10.99.10.99
You've hit kubia-gq7bc

[root@ip-172-31-28-137 04-controllers]# curl -k http://10.99.10.99
curl: (7) Failed to connect to 10.99.10.99 port 80 after 0 ms: Connection refused
 
 [root@ip-172-31-28-137 ec2-user]# kubectl get rs
NAME      DESIRED   CURRENT   READY   AGE
mavenir   3         3         3       130m
[root@ip-172-31-28-137 ec2-user]#
 
 [root@ip-172-31-28-137 ec2-user]# kubectl get svc
NAME         TYPE        CLUSTER-IP    EXTERNAL-IP   PORT(S)   AGE
kubernetes   ClusterIP   10.96.0.1     <none>        443/TCP   41h
kubia        ClusterIP   10.99.10.99   <none>        80/TCP    141m


 
