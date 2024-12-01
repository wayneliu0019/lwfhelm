
 用法：
 ```
 wayne@192  ~  helm repo add lwfhelm https://wayneliu0019.github.io/lwfhelm/
WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /Users/wayne/.kube/config
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /Users/wayne/.kube/config
"lwfhelm" has been added to your repositories

 wayne@192  ~  helm repo update
WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /Users/wayne/.kube/config
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /Users/wayne/.kube/config
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "lwfhelm" chart repository
Update Complete. ⎈Happy Helming!⎈

 wayne@192  ~  helm search repo hello-demo
WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /Users/wayne/.kube/config
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /Users/wayne/.kube/config
NAME              	CHART VERSION	APP VERSION	DESCRIPTION
lwfhelm/hello-demo	2.2          	1.17.0     	A Helm chart for Kubernetes
```

