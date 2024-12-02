
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
1. GitHub Releases 页面通常用于展示标有特定版本标签的存储库快照，以及与这个版本相关的二进制文件、包或其他类型的构建工件。通常，会在 Releases 页面上找到直接从存储库中生成的压缩源代码（zip 和 tar.gz 文件）以及**手动上传的工件**
1. 对于 Helm Chart，当使用 `helm/chart-releaser-action` 这类 GitHub Actions 自动添加 Helm Chart 作为 Release 版本时，Helm Chart 包（.tgz 文件）被推送到了项目的 GitHub Pages 指向的 Helm 仓库（通常是 `gh-pages` 分支）。
1. 创建一个release（v2.17.0），action执行完毕后，在release中会有2个release记录，名字分别为`v2.17.0`和`hello-demo-1.17.0`：
   <img width="1133" alt="image" src="https://github.com/user-attachments/assets/8a994bc8-694b-4f61-980c-1d0227d15cc5">
其中，一个是标准的源代码 Release（`v2.17.0`），只包含自动生成的源代码 zip 和 tar.gz，另一个是由 chart-releaser-action 生成的 Helm Chart Release（`hello-demo-1.17.0`），包含 Helm Chart的.tgz 文件。

* 标准源代码 Release：当您在仓库中打标签并推送时，GitHub 会自动为该标签创建一个 Release，并且包含源代码的 zip 和 tar.gz 文件。

* Helm Chart Release：helm/chart-releaser-action 会创建一个单独的 Release，专门用于存放和分发 Helm Chart 包。每当您的 Chart 版本变化时，chart-releaser-action 会识别 Chart 版本的变化，然后创建一个名为 ChartName-Version.tgz 的打包文件，并将其上传为相对应版本的 Release Assets。在 GitHub Actions 工作流定义中，该步骤通常使用特定的配置，使 chart-releaser-action 与存储库中的标签关联。
