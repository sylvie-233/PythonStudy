# Kubernetes

`【Udemy付费课程】 Docker and Kubernetes：P36`


## 基础介绍

一站式微服务集群管理，可替换部分SpringCloud组件
开源的容器编排平台，用于自动化部署、扩展和管理容器化应用程序
Google(SpringCloud版PM2工具)

**一切围绕着Pod进行的核心操作**（分布式版Docker-Composer）


一个Master Node主节点多个Worker Node工作节点
- Namespaces:
- Applications:
- Services:
- Ingresses:
- ConfigMaps:
- Secrets:
- Volume:


K8s集群划分:
Namespace(环境隔离) -> Ingress(网关) -> Service(服务注册、负载均衡) -> Deployment(pod副本、扩缩容) -> Pod -> Container

K8S集群搭建：
- minikube：
- k3s：
- 裸机安装：
    - kubeadm:
    - kubectl:
    - kubelet:
        - coredns
        - etcd
        - kube-apiserver
        - kube-controller-manager
        - kube-scheduler
        - kube-porxy
        - conformance: 验证确保集群实现符合 Kubernetes API 标准




![k8s架构图](../assets/k8s架构图.png)
![kubernetes-cluster-architecture](../assets/kubernetes-cluster-architecture.svg)
```yaml
- Cluster:
    - Master Node:
        - API Server: # 集群的入口，提供 REST API
            - ConfigMap: # 虚拟存储应用程序的配置信息
            - Ingress: # 用于管理集群外部如何访问集群内部的服务(Service)
        - Cloud Controller:  # 云平台相关管理(可选)
            - Service Controller:
        - Kube Controller: # 维护副本数、节点健康
            - CronJob Controller:
            - DaemonSet Controller: # 确保每个 Worker 节点上都有指定的 Pod 运行
            - Deployment Controller: # 资源对象，管理 Pod 创建、更新、扩缩容
            - Endpoint Controller:
            - HPA Controller:
            - Job Controller: # 负责 Job 资源，确保任务执行一次完成
            - Namespace Controller: # 逻辑上的资源隔离机制
            - Node Controller: # 监控 Worker 节点状态，发现失联节点
            - PVC Controller: # 绑定 PVC 到 PV，管理存储
            - ReplicaSet Controller: # 取代 ReplicationController，管理 Pod 副本
            - Replication Controller: # 确保 Pod 副本数符合 ReplicationController 设定
            - StatefulSet Controller: # 负责 StatefulSet 资源，保证有状态 Pod 正常运行
        - Scheduler: # 负责 Pod 的调度
        - Etcd: # 集成注册中心，保存集群状态
        - kubectl: # Kubernetes 命令行工具，用于管理集群
    - Worker Nodes:
        - Kubelet: # 负责与 Master 通信，管理 Pod
        - Kube-Proxy: # 负责网络代理和负载均衡，维护 Service 的网络规则，管理流量转发
        - Pods:
            - Containers: # docker 容器
            - Ingress Controller:
            - Custom Controller: #  自定义 Controller 以 Pod 形式运行在 Worker 节点，监听 CRD 资源变化，并执行相应的逻辑
```

默认存在两个命名空间 default、kube-system（flannel为dns插件创建的命名空间）

Controller控制器
- Deployment
- StatefulSet
- DaemonSet
- Job


k3d自动启动的容器：
- server：整个 Kubernetes 的控制平面节点
    - kube-apiserver
    - kube-controller-manager
    - kube-scheduler
    - etcd（或 SQLite）
    - k3s agent（也能跑 Pod）
- serverlb：一个小的 Traefik/Nginx 类似的 外部负载均衡器（让外部可以访问 k3s）
    - 暴露 Kubernetes API server 端口（你用 kubectl 访问的就是它）
    - 当你集群有多个 server 时，它能自动做负载均衡
    - 以后你配置 Ingress，也会通过这个入口访问
- registry：镜像仓库
- tools：辅助工具容器

- Controller控制器通过label标签关联Pods
- `k3d cluster create dev`创建轻量级k8s集群，要修改集群ip为127.0.0.1（要不然无法访问）
- k3d临时配置目录：`.config\k3d/kubeconfig-dev.yaml`，k8s配置目录：`~/.kube/config`
- k3d使用本地镜像必须先导入到集群里
- ingress默认使用traefik路由，常配合中间件实现路径替换
- 在测试网络连接问题时，可以先用port-forward测试service是否可以直连，再测试ingress是否连通
- Role定义在某个 Namespace 内对资源的权限，ClusterRole定义全局Cluster（集群级别）或特定资源的权限
- Role的使用必须使用RoleBinding绑定到具体的用户ServiceAccound
- Role、ServiceAccount、RoleBinding 这些本质上是为了 Pod 访问 Kubernetes API 时控制权限 而设计的
- 每个 Pod 在创建时都会默认绑定一个 ServiceAccount，Pod 内的应用就会以这个身份与 Kubernetes API 交互
    - 在每个命名空间（Namespace）都会自动创建一个名为 default 的 ServiceAccount。
    - 如果你没有手动指定 Pod 的 ServiceAccount，Pod 默认就使用这个 default



### kubectl
```yaml
kubectl: # 本质是向api-server发送REST请求
    apply: # 应用配置（有则更新、无则创建）
        -f: # 指定配置文件
    autoscale: # 自动扩缩容，HPA
    cluster-info: # 集群信息
    config:
        get-contexts: # 获取集群上下文列表
        use-context: # 切换集群上下文
        view: # 查看k8s配置
    cp:
    create: # 创建（有则报错）
        -f: # 根据配制文件创建资源
        configmap:
            --from-file:
            --from-literal:
        deployment: # 创建 deploy 部署资源
            --image:
        namespace: # ns，命名空间
        secret:
            generic:
    debug:
    delete: # 删除
        -f: # 指定配置文件删除
        deployment: # 创建部署资源
            --cascade: # 级联删除
            --image:
        namespace:
        pod: # 删除 pod
        pods:
        services:
        statefulset:
            --cascade: # 级联删除pod
    descibe: # 查看详细信息
        pod: # 查看pod详情
    edit: # 编辑配置
    exec: # 在指定pod中执行命令 (-it -- bash 默认进入pod的第一个容器)
        -c: # 指定容器
        -i:
        -t:
    expose: # 暴露
        deployment: # 暴露部署资源
            --port:
            --type:
                NodePort:
    describe: # 查看配置和运行事件信息
        deployment:
        node: # 查看某个节点的详细信息
        pods: # po
            -n:
        svc:
    get:
        -A: # 所有命名空间
        -l: # 指定标签（支持表达式）
            in:
            notin:
        -n: # 指定命名空间
        -o: # 输出
        -w: # 监听
        all: # 获取所有东西
        clusterrole:
        componentstatus: # 组件状态
        configmap: # cm
        cronjob:
        deployments: # deploy部署资源
        endpoints:
        events:
        nodes: # no，获取集群节点信息
            --show-labels: # 查看节点标签（用于pod节点选择）
        namespace: # ns，查看当前集群中的命名空间
        pods: # po，pod容器（默认查看默认命名空间default下）
            -l: # 根据标签匹配
            -n: # 指定命名空间
                kubesystem:
            -o: # 输出信息
                yaml: # 输出pod的yaml配置
            --show-labels: # 查看pod标签 
        pv: # 持久卷
        pvc: # 持久卷申领
        replicaset: # 副本集
        role:
        serviceaccount:
        services: # svc,service 服务
        statefulset:
        storageClass:
    label: # 打标签（name- 则为删除）
        --overwrite: # 覆盖标签（默认追加）
        nodes: # 节点打标签
        pods: # po 修改pod标签
    logs: # 日志查看
        -f: # 指pod
    patch: # 修改配置
    port-farward: # 端口转发（常用于测试）
    replace:
    rollout: # 版本滚动更新
        history: # 滚动历史
            --revision: # 回滚到指定版本的历史记录
        pause: # 更新暂停
        restart: # 重启
            deployment: # deploy
        resume: # 恢复执行
        status:
            deployment:
        undo: # 回滚上一个版本
            --to-revision: # 回滚指定版本
            deployment:
    run: # 运行创建pod
        --images:
    scale: # 扩缩容
        deployment: # deployment部署
            --replicas: # 副本数
        statefulset: # sts
    set: # 直接修改配置
        image: # 修改镜像
    taint: # 设置污点
        nodes: # 给节点设置污点
    top: # 资源使用信息
        nodes:
        pod:
    version:
``` 

Kubernetes 的命令行工具，⽤于 管理集群、部署应用、监控资源、调试问题 等


### kubeadm
```yaml
kubeadm:
    config:
        images:
            pull:
    init: # 初始化主节点
        --apiserver-advertise-address: # apiserver地址（建议）
        --image-repository:
        --kubernetes-version:
        --pod-network-cidr:
        --service-cidr:
    join: # worker节点加入集群
        --discovery-token-ca-cert-hash:
        --token: # 指定token
    reset:
        -y:
    token:
        list:
```

集群管理命令


### kubelet
```yaml
kubelet:

```



### minikube
```yaml
minikube:
    dashboard:
    delete:
        --all:
    service:
    start:
    stop:
```


### k3s


- k3s server
- k3s agent


### k3d
```yaml
k3d:
    --version:
    cluster:
        create: # 创建k8s集群
            -p: # 本机端口映射
            --api-port: # 本机cluster ip
            --config: # 指定配置文件
            --k3s-arg: # TLS SAN 设置
            --volume: # 本机server目录挂载
        delete: # 删除集群
        edit: # 编辑集群
            --port-add: # 端口暴露
        list: # 列出集群
            -o:
                json: # 输出json
        start:
        stop: # 停止集群
    image:
        import: # 导入镜像到k3d中
            -c: # 指定集群
    kubeconfig: # k8s配置 `~/.kube/config`
        get:
        merge: # 
            --overwrite:
```

k3s in docker

#### config
```yaml
config:
    apiVersion: v1
    kind: # Config
    preferences: {}
    clusters:   # 集群列表
        name: # 集群名称
        cluster: # 集群配置 
            server: # API server 地址
            certificate-authority-data: # CA 证书，用于验证 server 身份
    users:      # 用户/凭证列表
        name:
        user:
            client-certificate-data: # client 证书
            client-key-data: # client 私钥
    contexts:   # 上下文列表
        name:
        context:
            cluster:
            user:
            namespace: # 没有就是default
    current-context: # 当前上下文
```

```
kubectl 命令
       │
       ▼
  使用 current-context
       │
       ▼
  context -> 指定 cluster 和 user
       │
       ▼
  cluster -> API server 地址 + CA 证书
  user    -> client 证书 / token / 密码
       │
       ▼
   访问 Kubernetes API
```
.kube/config 文件是 kubectl 的配置文件：用于告诉 kubectl（以及其他客户端库）
1. 去哪个 Kubernetes 集群（cluster）
2. 用什么身份访问（user / ServiceAccount / client certificate）
3. 在什么命名空间操作（context）
4. 选择默认操作的上下文（current-context）




## 核心内容
```yaml
Kubernetes:
    --- # Master
    API Server: # 接口服务，基于REST
    Kube Controller Manager: # 控制器管理器
    Cloud Controller Manager: # 云控制器管理器
    Kube Scheduler: # pod调度器
    Etcd: # 分布式KV数据库
    --- # Node
    Kubelet:
    Kube Proxy:
    Container Runtime: # 容器运行时环境
    Pod: # 容器组
    --- # Resource资源
    HPA: # Pod自动扩容
    PodTempalte:
    LimitRange:
    Namespace:
    Node:
    ClusterRole:
    ClusterRoleBinding:
    Pod:
        Replication Controller: # RC
        ReplicaSet: # RS，动态更新Pod副本数，RC进阶版，基于Selector、Label机制
        Deployment: # RS进阶版，自动创建RS，支持滚动升级、回滚、暂停、恢复
        StatefulSet: # 有状态服务，
            Headless Service: # 服务名、ip绑定
            VolumeClaimTemplate: # 持久化存储卷模板
        DaemonSet: # 为每一个匹配的Node都部署一个守护进程
        Job:
        CronJob:
    Service: # K8s内部网络调用
    Ingress: # K8s内部服务暴露给外网访问
    Volume: # 数据卷
    CSI:
    ConfigMap: # K-V配置
    Secret:
    DownwardAPI:
    Role: # 权限
    RoleBinding:
```


多个 Node 组成的 Kubernetes 集群，包括 Master 节点和 Worker 节点


### Api Server

kubectl调用的rest服务

api版本：alpha、beta、stable、



### Scheduler




### Kube Controller Manager


- 节点控制器
- 任务控制器
- 端点分片控制器
- 服务账号控制器



### Cloud Controller Mangager


- 节点控制器
- 路由控制器
- 服务控制器


### Etcd


## 工作负载资源

(Workload Resources)
用于定义和管理容器化应用的工作负载。

### Pod
```yaml
pod.yaml:
    apiVersion:
    kind:
        pod:
    metadata: # pod相关元数据
        annotations:
        generation:
        labels: # 标签，用于selector
        name:
        namespace: # 命名空间，默认default
        resourceVersion:
        uid:
    spec:
        affinity: # 亲和性
            nodeAffinity: # 节点亲和性
                preferredDuringSchedulingIgnoreDuringExecution: # 软亲和性
                    preference:
                        matchExpressions:
                            key:
                            operator:
                            values:
                    weight: # 软亲和性权重
                requiredDuringSchedulingIgnoreDuringExecution: # 硬亲和性
                    nodeSelectorTerms:
                        matchExpressions:
                            key:
                                cpu:
                                ssd:
                            operator:
                                Exists:
                                In:
                                NotIn:
                            values:
            podAffinity: # pod亲和性
                requiredDuringSchedulingIgnoredDuringExecution:
                    labelSelector:
                        matchExpressions:
                    topologyKey:
            podAntiAffinity: # pod反亲和性
        containers: # pod中容器
            args:
            env: # 环境变量
                name:
                valueFrom:
                    configMapKeyRef: # configMap值引用
                        name:
                        key:
                    secretKeyRef: # secret值引用
                        name:
                        key:
            command:
            image: # 容器镜像
            imagePullPolicy: # 镜像拉取策略
                IfNotPresent: # 如果不存在    
            lifecycle: # 生命周期钩子
                postStart:
                    exec:
                        command:
                preStop:
            livenessProbe: # 探针
                httpGet:
                    path:
                    port:
                    schema:
            name: # 容器名称
            ports: # 端口
                containerPort: # 容器端口
                name:
                protocol:
            readinessProbe: # 探针
                httpGet:
            resources:
                limits: #
                    memory:
                requests: # 必须资源
                    cpu:
                    memory:
            startupProbe: # 探针
                exec:
                    command:
                httpGet:
            volumeMounts: # 数据卷挂载
                mountPath: # 容器内需要挂载路径
                name: # 挂载的数据卷
                readOnly:
            workingDir: # 工作目录
        hostNetwork:
        imagePullSecrets: # image拉取密钥
        initContainers:
            command:
            image:
            name:
        nodeName: # 指点调度的节点名称
        nodeSelector: # 节点选择
            cpu:
            diskType: # 磁盘要求
                ssd:
        restartPolicy: # 重启策略
            Always:
        tolerations: # 容忍污点
            effect:
            key:
            operator:
            tolerationSeconds: # 容忍时间
            value:
        volumes: # 定义数据卷
            configmap:
                items:
                    key:
                    path:
                name:
            emptyDir: # 同一个pod不同的容器共享目录
            hostPath: # 与主机共享目录
                path: # 主机节点路径
                type:
                    DirectoryOrCreate:    
            name: # 数据卷名称
            nfs: # 网络文件系统
                path: # nfs路径
                readOnly:
                server: # nfs服务地址
            persistentVolumeClaim: # 关联PVC
                claimName: # pvc名称
            secret:
                secretName:
```

最小的部署单元，包含一个或多个容器(多个容器之间共享上下文)
每个Pod内部内置一个Pause容器


每个pod有自己唯一的ip地址、在集群内部
- Pod配置文件
- Pod探针
- Pod生命周期


Pod探针：容器内应用监控机制（钩子函数）
- StartupProbe:
- LivenessProbe:
- ReadinessProbe:

Pod探针探测方式：
- ExecAction:
- TCPSocketAction:
- HTTPGetAction:

Pod生命周期钩子：
- 初始化阶段：initContainers
- PostStart:
- preStop:


#### Label

基于标签分组


#### LifeCycle

pod生命周期
- Pending
- Running
- Succeeded:
- Failed：
- Unknown：


#### Affinity

亲和性
- nodeAffinity：节点亲和性
    - preferredDuringSchedulingIgnoreDuringExecution：软亲和性
    - requiredDuringSchedulingIgnoreDuringExecution：硬亲和性
- podAffinity：pod间亲和性
- podAntiAffinity：


#### Taint

节点污点
Pod容忍污点



#### NodeSelector

Pod节点选择


#### RestartPolicy


Pod重启策略


#### InitContainer

特殊容器，在Pod内的应用容器启动之前运行


#### Container

Pod容器

##### LifeCycle


容器生命周期：
- Waiting
- Running
- Terminated


容器生命周期回调
- postStart
- preStop




##### Probe

容器生命周期探针：
- livenessProbe:
- readinessProbe：
- startupProbe：
    - exec
    - tcpSocket
    - httpget
    - grpc

##### Resource

资源限制
- request
- limit
    - memory
    - cpu


##### Command

启动执行命令



#### Volume

数据卷挂载





### ReplicaSet

Pod副本机制
确保指定数量的 Pod 副本始终运行





### Deployment
```yaml
deployment.yaml:
    apiVersioin:
    kind:
    metadata:
    spec:
        replicas: # 副本数
        revisionHistoryLimit: # 滚动更新保留的历史版本数
        selector: # pod选择器
            matchLabels:
        strategy: # 更新策略
            rollingUpdate:
            type:
        template: # pod模板
            metadata:
                labels:
            spec:
                containers:
                dnsPolicy:
```

pod部署资源：Deployment = Pod + ReplicaSet
Pod功能增强：
- Deployment 是通过创建 ReplicaSet 来管理 Pod 的
- 提供声明式更新，管理 ReplicaSet 和 Pod。
- 支持扩缩容
- 滚动更新：修改pod template自动触发
- 版本回退

![k8s_deployment运行](../assets/k8s_deployment运行.png)


Deployment常用于无状态服务


### StatefulSet
```yaml
statefulset.yaml:
    apiVersion:
    kind: # StatefulSet
    metadata:
    spec:
        replicas:
        serviceName: # 服务名称
        template: # pod模板
            metadata:
            spec:
                containers:
                    image:
                    name:
                    ports:
                    volumeMounts: # 数据卷
                        mountPath: # 加载到哪个目录中
                        name: # 要加载的数据卷名称
        updateStrategy: # 更新策略
            rollingUpdate:
                partition: # 需要更新的分区>=
            type:
        volumeClaimTemplate: # volume数据卷模板
            metadata:
            spec:
                accessNodes:
                resources:
                    requests:
                        storage:
```

类似Deployment
管理有状态应用的部署和扩展，确保 Pod 的唯一性和顺序性。
有状态Pod管理增强：StatefulSet = Pod + PVC + Service
- Pod名称编号：	固定顺序，如 mysql-0, mysql-1
- Pod有序启动/销毁（0 → 1 → 2）
- 每个 Pod 有固定 hostname、DNS
- 每个 Pod 绑定自己的 PVC（持久卷）
- StatefulSet 不依赖 ReplicaSet，它有自己的 Pod 管理机制
- 删除 StatefulSet 时默认不会删除它的 Pod（孤儿 Pod）


StatefulSet常用于有状态服务（数据库）



### DaemonSet
```yaml
daemonset.yaml:
    apiVersion:
    kind:
    metadata:
        name:
    spec:
        selector: # 选择器，要注入哪些pod
            matchLabels:
                labels:
                    name:
        template: # pod 模板，要注入的pod
            metadata:
                labels:
                name:
            spec:
                containers:
                    env:
                    volumeMounts: # 数据卷使用
                        mountPath:
                        name:
                nodeSelector: # 选择器，要注入到哪些node上
                    type:    
                volumes: # 定义数据卷
                    hostPath:
                    name:

```

基于Node Selector机制，给指定node注入一个pod（守护进程）
确保所有或部分节点运行一个 Pod 副本，通常用于系统级守护进程。


### HPA

Pod水平自动扩缩容
基于监控机制，通过观测pod的cpu、内存使用率、自定义metrics指标进行的自动扩缩容pod的数量（前提是pod必须配置了resources资源）


### Job

创建一次性任务，确保任务完成。

### CronJob
```yaml
cronjob.yaml:
    apiVersion:
    kind:
    metadata:
        name:
    spec:
        concurrencyPolicy:
        failedJobsHistoryLimit:
        suspend:
        schedule:
        jobTemplate:
            spec:
                template:
                    spec:
                        containers:
                            name:
                            image:
                            command:
                        restartPolicy:
```

基于时间表创建 Job，用于定时任务。
(分、时、日、月、周)

### ReplicationController (已弃用)

早期用于管理 Pod 副本，现被 ReplicaSet 取代。

## 服务资源

(Service Resources)
用于定义和管理网络服务。

### Service
```yaml
service.yaml:
    apiVersion:
    kind:
    metadata:
        name:
        labels:
    spec:
        selector: # pod选择
        ports: # 端口转发
            name:
            port: # service对外暴露给其它port使用的端口
            targetPort: # 目标pod内容器的端口
            nodePort: # pod暴露到node节点端口
        type: # 类型
            ClusterIP: # 配置为None则不分配ip，只能通过服务名访问
            Headless:
            LoadBalance:
            NodePort:
```

服务反向代理

内部代理：实现了 service服务名 到 pod ip 的映射
Service -> Endpoint -> Kube Proxy -> Pod -> Pause Container


基于selector，聚合对指定pod的网络访问
- Service 是一个抽象定义，Service 通过 Endpoints 实现流量转发到对应 Pod
- 所有匹配的pod都可以通过service进行访问
- 依赖endpoint对ip port的存储信息



提供稳定的网络端点，用于访问 Pod。
配合pod副本可实现负载均衡




#### ClusterIP

集群内部访问。
- Pod 的 IP 是动态变化的，不适合直接访问
- Service 的 ClusterIP 是固定的，适合作为访问入口
- 后端 Pod 可以随时伸缩，Service 自动更新 Endpoints 来适配

#### NodePort

通过暴露节点端口访问。
Kubernetes 会让每个物理节点打开一个端口（比如 30080），作为从外部进入集群的统一入口点，然后通过 kube-proxy 把请求转发到对应的 Pod 上

#### LoadBalancer

通过云提供商的负载均衡器访问。

#### ExternalName

将服务映射到外部 DNS 名称。

### Ingress
```yaml
ingress.yaml:
    apiVersion:
    kind:
    metadata:
        name:
    spec:
        rules: # 路由规则
            host: # 主机名，域名
            http: # 基于http规则
                paths: # 路径规则配置
                    backend:
                        serviceName: # 转发到的service
                        servicePort:
                    path: # /xxx 访问的url
                    pathType: # 路径类型
                        Prefix: # 路径前缀

```

网关
管理外部访问集群服务的 HTTP/HTTPS 路由。


#### Middleware

路由中间件

##### StripPrefix

url前缀替换


### IngressClass

定义 Ingress 控制器的类型。

### Endpoint
```yaml
endpoint.yaml:
    apiVersion:
    kind:
    metadata:
        labels: # 与service相同
        name:
        namespace:
    subsets:
        addresses:
            ip: # 目标ip存储
        ports:
            name:
            port:
            protocol:
```

服务注册、发现机制：
存储 Service 对应的 Pod IP 和端口。

每当有 Pod 创建或删除时，Kubernetes 的 kube-controller-manager 中的 Endpoints Controller 会：
- 查找所有匹配 app: my-app 的 Pod
- 把这些 Pod 的 IP + Port 注册到 Service 的 Endpoints 对象中

### EndpointSlice

更高效的 Endpoint 管理方式，支持大规模集群。

## 配置资源

(Configuration Resources)

用于配置应用和集群。

### ConfigMap
```yaml
configMap.yaml:
    apiVersion:
    kind:
    metadata:
    data: # 自定义kv配置
```

存储非敏感配置数据，如环境变量、配置文件等。
支持热更新加载配置文件


### Secret
```yaml
secret.yaml:
    apiVersion:
    kind:
    metadata:
    type:
    data:
```

存储敏感信息，如密码、令牌、密钥等。

### ResourceQuota

限制命名空间的资源使用(如 CPU、内存、Pod 数量等)。

### LimitRange


限制命名空间中资源的使用范围(如单个 Pod 的资源请求和限制)。

### HorizontalPodAutoscaler(HPA)

根据 CPU 使用率或其他自定义指标自动扩展 Pod 副本数。

## 存储资源


(Storage Resources)

用于定义和管理存储。

### PersistentVolume(PV)
```yaml
persistentvolume.yaml:
    apiVersion:
    kind:
    metadata:
        name: # pv名称
    spec:
        accessModes: # PV访问模式
        capacity: # 容量
            storage:
        local: # 本地存储
            path:
        mountOptions:
        nfs: # nfs存储
            path:
            server:
        nodeAffinity: # 节点亲和性
        persistentVolumeReclaimPolicy:
        storageClassName: # PV存储类，可自定义
        volumeMode: # 数据卷模式
            Filesystem:
        
```

持久卷：磁盘资源抽象
集群中的存储资源，由管理员配置。


#### StorageClass
```yaml
storageClass.yaml:
    apiVersion:
    kind:
    metadata:
    provisioner:
    parameters:
        type:
    volumeBindingMode:
```

定义存储类型和配置，支持动态创建 PV。
依赖制备器策略：具体底层使用哪种存储（自定义容器）




### PersistentVolumeClaim(PVC)
```yaml
persistentvolumeclaim.yaml:
    apiVersion:
    kind:
    metadata:
        name:
    spec:
        accessModes: # 访问模式
            ReadWriteOnce: # pod独占式
        volumeMode: # 数据集模式
        resources: # 申请资源大小
            requests:
                storage:
        storageClassName: # 存储类，和PV中一致
```

持久卷申领：申请使用持久卷
用户对存储资源的请求，绑定到 PV。



### Volume

Pod 中的存储卷，支持多种类型(如 emptyDir、hostPath、NFS 等)。



#### HostPath


#### EmptyDir

用于同一个pod中不同容器共享


#### NFS

网络文件系统挂载


### VolumeSnapshot

存储卷的快照。

### VolumeSnapshotClass

定义存储卷快照的类型。





## 安全资源

(Security Resources)
用于管理和控制安全性。

### ServiceAccount

为 Pod 提供身份，用于与 API Server 交互。
默认default账户


### Role
```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: pod-reader
rules:
- apiGroups: [""]     # "" 表示 core API，如 Pod、Service
  resources: ["pods"]
  verbs: ["get", "list", "watch"]
```

定义命名空间内的权限。

### ClusterRole

定义集群范围内的权限。

### RoleBinding
```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-pods-binding
  namespace: default
subjects:
- kind: User          # 可以是 User / Group / ServiceAccount
  name: alice
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role          # 关联 Role 或 ClusterRole
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```

将 Role 绑定到用户、组或 ServiceAccount。

### ClusterRoleBinding

将 ClusterRole 绑定到用户、组或 ServiceAccount。

### PodSecurityPolicy(PSP) (已弃用)


定义 Pod 的安全策略。

### NetworkPolicy

控制 Pod 之间的网络通信。

### CertificateSigningRequest(CSR)

用于请求证书签名。

## 策略资源

(Policy Resources)

用于定义和管理策略。

### PodDisruptionBudget(PDB)

限制自愿中断(如升级或维护)对应用的影响。

### ResourceQuota

 限制命名空间的资源使用。

### LimitRange


限制命名空间中资源的使用范围。


## 调度资源

(Scheduling Resources)

用于调度和管理 Pod 的放置。

### Taint


污点（给节点配置）
标记节点，防止 Pod 调度到该节点。

节点控制器，在某些状态下会自动设置一些污点

污点行为effect：
- NoSchedule	不会调度新的 Pod 到这个节点（除非 Pod 有容忍）
- PreferNoSchedule	尽量不要调度Pod 到这个节点，但不是强制的
- NoExecute	不仅阻止新 Pod 被调度，还会驱逐（Evict）已经运行的非容忍的 Pod

### Toleration

容忍（给pod配置，容忍带污点的节点）
允许 Pod 调度到有特定 Taint 的节点。
- Equal
- Exists

### Affinity

亲和性（物体之间接受程度）
Anti-Affinity
定义 Pod 与节点或其他 Pod 的亲和性或反亲和性。

### PriorityClass

 定义 Pod 的调度优先级。

## 监控和日志资源

(Monitoring and Logging Resources)
用于监控和日志记录。

### HorizontalPodAutoscaler(HPA)

 根据 CPU 使用率或其他自定义指标自动扩展 Pod 副本数。

### Metrics Server

 收集和提供资源使用指标。

### Custom Metrics API

 支持自定义指标。

### Event


 记录集群中的事件。

## 元资源


(Meta Resources)
用于管理和组织其他资源。

### Namespace

 将资源分组到虚拟集群。

### Label

 键值对，用于标识和选择资源。

### Annotation

 键值对，用于存储非标识性元数据。

### Finalizer

 控制资源的删除行为。

## 扩展资源


(Extension Resources)
用于扩展 Kubernetes 功能。

### CustomResourceDefinition (CRD)

 定义自定义资源。

### Operator

 使用 CRD 和控制器管理复杂应用。

### APIService

 扩展 Kubernetes API。

## 集群管理资源


(Cluster Management Resources)
用于管理集群本身。

### Node

 集群中的工作节点。


#### Kubelet



#### Kube-Proxy





### Namespace

 将资源分组到虚拟集群。

### ClusterRole

 定义集群范围内的权限。

### ClusterRoleBinding

 将 ClusterRole 绑定到用户、组或 ServiceAccount。

### ComponentStatus

 显示集群组件的状态。

## 云原生生态相关资源

Kubernetes 生态系统中还有许多扩展资源，通常由第三方工具或插件提供：






### Prometheus

监控指标数据和告警。

#### Grafana

可视化指标


### ELK

日志


### Fluentd


Fluent Bit

日志收集。

### Istio

 服务网格。

### Knative

 无服务器计算。

### ArgoCD

 GitOps 持续交付。


## 管理平台


### Dashboard



### Kubesphere


### Kuboard


## Helm
```yaml
helm:
    create:
    dependency:
    history:
    install: # 安装
        --set: # 修改参数
    lint:
    list: # ls
    package:
    pull:
    repo: # 仓库管理
        add:
        list:
    rollback:
    search: # 搜索
        hub: # 官方仓库
        repo: # 第三方仓库
    show:
        readme:
    uninstall:
    upgrade:
```


k8s包管理工具
基于K8s的一整套项目解决方案


### 项目结构
```yaml
项目结构:
    /charts:
    /templates:
    .helmignore:
    Chart.yaml: # .Chart
    values.yaml: # 变量定义.Values
```


### Chart

Helm包



### Release

helm包实例
