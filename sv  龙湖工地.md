## sv  龙湖工地

#### k3s 固件内版本（v1.0.7）需升级为（v1.0.8）

#### k3s 启动参数需更新

```shell
${workspace}/k3s agent \
    --run-mode join_k3s \
    --server https://192.168.254.250:6443 \
    --cluster-secret aibee_edge_secret \
    --kubelet-arg eviction-hard="imagefs.available<5%,memory.available<100Mi,nodefs.available<5%,nodefs.inodesFree<5%" \
    --kubelet-arg kube-reserved="cpu=100m,memory=100Mi,ephemeral-storage=100Mi" \
    --kubelet-arg system-reserved="cpu=100m,memory=100Mi,ephemeral-storage=100Mi" \
    --kubelet-arg pod-infra-container-image=k8s/pause:3.1 \
    --kubelet-arg containerd=/run/k3s/containerd/containerd.sock \
    --pause-image="k8s/pause:3.1" \
    --registry=http://192.168.254.250:5000 \
    --node-name  ${node_ip} \
    --node-ip  ${node_ip} \
    --node-label "device=camera" \
    --data-dir /mnt/nfs0/k3s

sleep 10
rm -rf /mnt/nfs0/k3s/data
```



## sv common-push 配置

```shell
project_id: LONGFOR_xuzhou_gongdi_trafficlite
site_id: LONGFOR_xuzhou_gongdi


group_id: LONGFOR_xuzhou_gongdi
product_id: trafficlite
face_id_push:
  server: https://cp-stage.aibee.cn
  port: 443
  url: /v1/match
  key: Obpa9wQia7irWm0Pd8v53fxesrynKiHX
  secret: 2QCbUXkBlMb6ywl7dAyfc2BjG05lPn10
  queue_size: 500
```

