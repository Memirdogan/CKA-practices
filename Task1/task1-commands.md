k create namespace cka-task1
k create namespace cka-task1 --dry-run=client -o yaml > cka-task1-namespace.yaml
k apply -f cka-task1-namespace.yaml
k create deployment task1 --image=busybox --replicas=1 --namespace=cka-task1 --dry-run=client -o yaml > task1-deployment.yaml
(*edit to deployment yaml*)
k apply -f task1-deployment.yaml

[*checked to deployment and pods*]
k get all                                 ✔ ╱ 4s  ╱ minikube/cka-task1 󱃾
NAME                        READY   STATUS    RESTARTS   AGE
pod/task1-95bcd9d9c-rdbzf   2/2     Running   0          23s

NAME                    READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/task1   1/1     1            1           23s

NAME                              DESIRED   CURRENT   READY   AGE
replicaset.apps/task1-95bcd9d9c   1         1         1       23s

[*check to logs*]
k logs deployments/task1 task1-app               ✔ ╱ minikube/cka-task1 󱃾
[INFO][STDOUT] current time is: Sat Feb  1 20:09:38 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:09:43 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:09:48 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:09:53 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:09:58 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:10:03 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:10:08 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:10:13 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:10:18 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:10:23 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:10:28 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:10:33 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:10:38 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:10:43 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:10:48 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:10:53 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:10:58 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:11:03 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:11:08 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:11:13 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:11:18 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:11:23 UTC 2025
[INFO][STDOUT] current time is: Sat Feb  1 20:11:28 UTC 2025

  ╱  ~/De/CKA-practices/Task1 ╱   main !1  k logs deployments/task1 task1-sidecar           ✔ ╱ minikube/cka-task1 󱃾
[INFO][FILELOG] current time is: Sat Feb  1 20:09:38 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:09:43 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:09:48 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:09:53 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:09:58 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:10:03 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:10:08 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:10:13 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:10:18 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:10:23 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:10:28 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:10:33 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:10:38 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:10:43 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:10:48 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:10:53 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:10:58 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:11:03 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:11:08 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:11:13 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:11:18 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:11:23 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:11:28 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:11:33 UTC 2025
[INFO][FILELOG] current time is: Sat Feb  1 20:11:38 UTC 2025

[*Describe pod*]
k describe pod task1-95bcd9d9c-rdbzf             ✔ ╱ minikube/cka-task1 󱃾
Name:             task1-95bcd9d9c-rdbzf
Namespace:        cka-task1
Priority:         0
Service Account:  default
Node:             minikube/192.168.49.2
Start Time:       Sat, 01 Feb 2025 23:09:32 +0300
Labels:           app=task1
                  pod-template-hash=95bcd9d9c
Annotations:      <none>
Status:           Running
IP:               10.244.0.3
IPs:
  IP:           10.244.0.3
Controlled By:  ReplicaSet/task1-95bcd9d9c
Containers:
  task1-app:
    Container ID:  docker://0fb37cfd18d92f41ea03cf8340aac9181e403308794d9e27136bb95e5facbe2b
    Image:         busybox
    Image ID:      docker-pullable://busybox@sha256:a5d0ce49aa801d475da48f8cb163c354ab95cab073cd3c138bd458fc8257fbf1
    Port:          <none>
    Host Port:     <none>
    Command:
      /bin/sh
      -c
      while true; do echo "[INFO][STDOUT] current time is: $(date)"; echo "[INFO][FILELOG] current time is: $(date)" >> /var/log/app.log; sleep 5; done
    State:          Running
      Started:      Sat, 01 Feb 2025 23:09:38 +0300
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/log from log-volume (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-29pw9 (ro)
  task1-sidecar:
    Container ID:  docker://6e2e6b3357d6bc72e89d4d26d6be8d37d99f017f686ea5c3de2c75f68974e654
    Image:         busybox
    Image ID:      docker-pullable://busybox@sha256:a5d0ce49aa801d475da48f8cb163c354ab95cab073cd3c138bd458fc8257fbf1
    Port:          <none>
    Host Port:     <none>
    Command:
      /bin/sh
      -c
      tail -n+1 -F /var/log/app.log
    State:          Running
      Started:      Sat, 01 Feb 2025 23:09:41 +0300
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/log from log-volume (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-29pw9 (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True
  Initialized                 True
  Ready                       True
  ContainersReady             True
  PodScheduled                True
Volumes:
  log-volume:
    Type:       EmptyDir (a temporary directory that shares a pod's lifetime)
    Medium:
    SizeLimit:  <unset>
  kube-api-access-29pw9:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age    From               Message
  ----    ------     ----   ----               -------
  Normal  Scheduled  4m47s  default-scheduler  Successfully assigned cka-task1/task1-95bcd9d9c-rdbzf to minikube
  Normal  Pulling    4m45s  kubelet            Pulling image "busybox"
  Normal  Pulled     4m41s  kubelet            Successfully pulled image "busybox" in 4.105s (4.105s including waiting). Image size: 4269694 bytes.
  Normal  Created    4m41s  kubelet            Created container: task1-app
  Normal  Started    4m41s  kubelet            Started container task1-app
  Normal  Pulling    4m41s  kubelet            Pulling image "busybox"
  Normal  Pulled     4m38s  kubelet            Successfully pulled image "busybox" in 2.412s (2.412s including waiting). Image size: 4269694 bytes.
  Normal  Created    4m38s  kubelet            Created container: task1-sidecar
  Normal  Started    4m38s  kubelet            Started container task1-sidecar


