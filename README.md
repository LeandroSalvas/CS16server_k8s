# Counter-Strike 1.6 Server K8s(Kubernetes)

# NOTICE

The Network Service used on this solutionn is based on MetalLB, so if your k8s cluster use a different solution you'll need to adapt to use your network service.


## Files

### Deployment
* cs16-deployment.yaml -  ServerApplication

### Config Maps
* cs16-cm0-configmap.yaml - users.ini
* cs16-cm1-configmap.yaml - motd.txt
* cs16-cm2-configmap.yaml - mapcycle.txt
* cs16-cm3-configmap.yaml - server.cfg

### Services
* cs16-service.yaml - Network Services


## How-To

Clone Repository:
```
git clone https://github.com/LeandroSalvas/CS16server_k8s.git
```
change to directory of cloned repo:
```
cd CS16server_k8s
```
apply the deployment, config maps and services to K8s with following command:
```
kubectl apply -f cs16-service.yaml,cs16-deployment.yaml,cs16-cm0-configmap.yaml,cs16-cm1-configmap.yaml,cs16-cm2-configmap.yaml,cs16-cm3-configmap.yaml 
```




## run kubectl get pods until the pod status is Running
```
kubectl get pods
NAME                                               READY   STATUS    RESTARTS   AGE
cs16-686f864bcd-l9vff                              1/1     Running   1          5h34m
```

## Get LoadBalancer IP to connect on POD
```
kubectl get svc
NAME                              TYPE           CLUSTER-IP       EXTERNAL-IP      PORT(S)           AGE
cs16                              LoadBalancer   10.101.191.86  ` 192.168.15.243   27015:30840/UDP   6h6m
```

## How to test Server

Download Counter-Strike 1.6 on Steam 
Open Game and open console and type: connect (EXTERNAL-IP)
Wait for game connect and Voilà
