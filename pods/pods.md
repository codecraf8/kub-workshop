#### 1. Kubernetes intro

1. kubectl run nginx --image=nginx:1.10.0

2. kubectl get pods

3. kubectl expose deployments nginx --port 80 --type NodePort

4. kubectl get services

5. kubectl create -f podsbase.yaml

6. kubectl get pods

7. kubectl describe <podname>

8. kubectl port-forward <podname> 10080:80

9. curl http://127.0.0.1:10080

10. kubectl logs <podname>

11. kubectl exec <podname> --stdin --tty -c <podname>
