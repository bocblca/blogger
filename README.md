# blogger
some study software articles for c# k8s go ...
## k8s pvc pending  storageclass
#### k8s 动态PVC创建后一直处于pending状态的原因
网上说的:编辑/etc/kubernetes/manifests/kube-apiserver.yaml 加上
spec: 
  containers:
  - command:
    - kube-apiserver
    - --feature-gates=RemoveSelfLink=false  
#### 这是一个原因，但并不能解决所有状况，很多情况是NFS client provider的image有问题
把被墙的地址改为：<br>
    containers:    <br>
        - name: nfs-client-provisioner    <br>
         image: registry.cn-hangzhou.aliyuncs.com/open-ali/nfs-client-provisioner:latest       <br>
重新启动或部署nfs-client-provisioner就可以了。
