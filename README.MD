List Of Kubernetes Most Useful Commands

1. Pods

$ kubectl get pods

$ kubectl get pods — all-namespaces

$ kubectl get pod monkey -o wide

$ kubectl get pod monkey -o yaml

$ kubectl describe pod monkey

2. Create Deployments

Create single deployment:
$ kubectl run monkey — image=monkey — record

3. Scaling PODs

$ kubectl scale deployment/POD_NAME — replicas=N

4. POD Upgrade and history

List history of deployments:

$ kubectl rollout history deployment/DEPLOYMENT_NAME

Jump to specific revision:

$ kubectl rollout undo deployment/DEPLOYMENT_NAME — to-revision=N

5. Services

List services:

$ kubectl get services 

Expose PODs as services (creates endpoints)

$ kubectl expose deployment/monkey — port=2001 — type=NodePort 

6. Volumes

List Persistent Volumes and Persistent Volumes Claims:

$ kubectl get pv

$ kubectl get pvc

7. Secrets

List Persistent Volumes and Persistent Volumes Claims:

$ kubectl get secrets

$ kubectl create secret generic — help

$ kubectl create secret generic mysql — from-literal=password=root

$ kubectl get secrets mysql -o yaml

8. ConfigMaps

List Persistent Volumes and Persistent Volumes Claims:

$ kubectl create configmap foobar — from-file=config.js

$ kubectl get configmap foobar -o yaml

9. DNS

List DNS-PODs:

$ kubectl get pods — all-namespaces | grep dns

Check DNS for pod nginx (assuming a busybox POD/container is running)

$ kubectl exec -ti busybox — nslookup nginx

Note: kube-proxy running in the worker nodes manage services and set iptables rules to direct traffic.

10. Ingress

List DNS-PODs:

$ kubectl get ingress

$ kubectl expose deployment ghost — port=2368

11. Horizontal Pod Autoscaler 

When heapster runs:

$ kubectl get hpa

$ kubectl autoscale — help

12. DaemonSets

$ kubectl get daemonsets

$ kubectl get ds

13. Scheduler

NodeSelector based policy:

$ kubectl label node minikube foo=bar

Node Binding through API Server:

$ kubectl proxy

$ curl -H “Content-Type: application/json” -X POST — data @binding.json http://localhost:8001/api/v1/namespaces/default/pods/foobar-sched/binding

14. Taints and Tolerations

NodeSelector based policy:

$ kubectl taint node master foo=bar:NoSchedule

15. Troubleshooting

$ kubectl describe

$ kubectl logs

$ kubectl exec

$ kubectl get nodes — show-labels

$ kubectl get events

16. Role Based Access Control

$ kubectl create role fluent-reader — verb=get — verb=list — verb=watch — resource=pods

$ kubectl create rolebinding foo — role=fluent-reader — user=minikube

$ kubectl get rolebinding foo -o yaml
