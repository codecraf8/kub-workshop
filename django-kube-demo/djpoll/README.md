1. docker build  -t  5ak3t/django-kube:v1 djpoll

2. kubectl run djpoll --image=5ak3t/django-kube:v1 --replicas=1 --port=8000 \
                       --labels='app=djangopoll,tier=frontend' \
                       --requests='cpu=100m,memory=64Mi' \
                       --env="GET_HOSTS_FROM=dns" \
                       --dry-run --output=yaml > django-deployment.yaml

3. kubectl create -f django-deployment.yaml

4. kubectl expose deployment djpoll --selector='app=djangopoll,tier=frontend' --type=NodePort \
                                     --dry-run --output=yaml > service.yaml

5. kubectl create -f service.yaml

6. docker build -t 5ak3t/frontend-nginx:v1 nginx

7. kubectl run djnginx --image=5ak3t/frontend-nginx:v1 --replicas=1 --port=80 \
                       --labels='app=djangopoll,tier=frontend' \
                       --requests='cpu=100m,memory=64Mi' \
                       --env="GET_HOSTS_FROM=dns" \
                       --dry-run --output=yaml > nginx-deployment.yaml

8. kubectl create -f nginx-deployment.yaml

9. kubectl expose deployment djnginx --selector='app=djangopoll,tier=frontend' --type=NodePort \
                                     --dry-run --output=yaml > service.yaml

10. kubectl create -f service.yaml

11. open "http://$(minikube ip):$(kubectl get service djnginx --output='jsonpath={.spec.ports[0].NodePort}')"




#=================

minikube start --memory=4096 --cpus=4
eval $(minikube docker-env)

$ docker-machine rm default
$ docker-machine create --driver virtual box default



$ docker-machine restart default      # Restart the environment
$ eval $(docker-machine env default)  # Refresh your environment settings
