
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

**注意：**
1. 打开Release页面中，其Asset中并没有生成的helm的tgz压缩包。
1. GitHub Releases 页面通常用于展示标有特定版本标签的存储库快照，以及与这个版本相关的二进制文件、包或其他类型的构建工件。通常，会在 Releases 页面上找到直接从存储库中生成的压缩源代码（zip 和 tar.gz 文件）以及**手动上传的工件**
1. 对于 Helm Chart，当使用 `helm/chart-releaser-action` 这类 GitHub Actions 自动添加 Helm Chart 作为 Release 版本时，Helm Chart 包（.tgz 文件）不一定会作为 Release 资源直接展示在 Releases 页面上, helm chart包被推送到了项目的 GitHub Pages 指向的 Helm 仓库（通常是 `gh-pages` 分支）。
1. 如果 hello-demo-1.2.0.tgz这个Helm Chart 被推送到了项目的 Helm 仓库中，而没有手动作为额外的 asset 上传到 Release 中（比如 release v2.3），那么这个helm chart的tgz文件在 Release 页面上不会直接展示为下载资源。
