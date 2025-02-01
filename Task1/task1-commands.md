k create namespace cka-task1
k create namespace cka-task1 --dry-run=client -o yaml > cka-task1-namespace.yaml
k apply -f cka-task1-namespace.yaml
k create deployment task1 --image=busybox --replicas=1 --namespace=cka-task1 --dry-run=client -o yaml > task1-deployment.yaml
