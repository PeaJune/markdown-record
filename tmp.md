

## nvidia depends

```shell
Dependencies:
adduser
dkms
libc6
libcairo2
libegl1
libgdk-pixbuf2.0-0
libgl1
libgles2
libglib2.0-0
libgtk-3-0
libjansson4
libopengl0
libpango-1.0-0
libpangocairo-1.0-0
libvdpau1
libwayland-client0
libwayland-server0
libx11-6
libxext6
libxxf86vm1
pkg-config
screen-resolution-extra
xorg-video-abi-23 | xorg-video-abi-20 | xorg-video-abi-19 | xorg-video-abi-18 | xorg-video-abi-15 | xorg-video-abi-14 | xorg-video-abi-13 | xorg-video-abi-12 | xorg-video-abi-11 | xorg-video-abi-10 | xorg-video-abi-8 | xorg-video-abi-6.0
xserver-xorg-core

In addition to the Debian package dependencies listed above, the correct kernel
headers package must be installed. DKMS builds the NVIDIA kernel module
targeting the currently running kernel. You can find the version of the
currently running kernel by running `uname -r`.

One way to make sure that the correct version of the headers package is
installed is through apt-get:
`sudo apt-get install linux-headers-$(uname -r)`

When installing via `dpkg`, the packages must be installed in the correct
order. If installing all the packages (both toolkit and driver packages), the
order would be:
1.  libnvidia-compute-410
2.  nvidia-utils-410
3.  nvidia-compute-utils-410
4.  nvidia-kernel-source-410
5.  nvidia-kernel-common-410
6.  nvidia-dkms-410
7.  libnvidia-decode-410
8.  libnvidia-encode-410
9.  libnvidia-fbc1-410
10. libnvidia-cfg1-410
11. xserver-xorg-video-nvidia-410
12. libnvidia-common-410
13. libnvidia-gl-410
14. libnvidia-ifr1-410
15. nvidia-driver-410
16. nvidia-modprobe
17. nvidia-settings
18. libxnvctrl0
19. libxnvctrl-dev
20. cuda-cluster-runtime
21. cuda-cluster-devel

```

```shell

LD_LIBRARY_PATH: /root/usr/lib:/root/usr/lib/aarch64-linux-gnu:/root/usr/local/lib:/root/usr/lib/lapack:/root/usr/lib/libblas:/lib:/root/run/lib
PYTHONPATH: /root/usr/lib/python2.7
PATH: /opt/aibee/hadoop-2.6.5/bin:/bin:/usr/bin:/dav:/sbin:/usr/sbin:/root/usr/bin:/root/usr/local/bin:/root/usr/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
cfg_name: /root/body_assets/generic_mall_test/generic_mall_test.cfg
2020-07-10 15:48:09,075 INFO {'msg': 'loading files from /root/body_assets/generic_mall_test/test/fid_nnie_0/unique.yaml'}
running generic_mall_test/test/fid_nnie_0 with version 0.2.577
CUDA_VISIBLE_DEVICES=0,1
OMP_NUM_THREADS=1
/root/run/AibeeBody /root/body_assets/generic_mall_test/test/base/fid_nnie /root/body_assets/generic_mall_test/test/fid_nnie_0 test-edge -1

```



## test

```shell
'mem=3072M console=ttyAMA0,115200 root=/dev/mmcblk0p3 rootfstype=ext4 ip=192.168.87.209:192.168.87.255:192.168.87.254:255.255.255.0:demo:eth0:off  rw rootwait blkdevparts=mmcblk0:1M(boot),32M(kernel),14436M(rootfs)'
```



hik 3559 arm64

服务目录： /dav/package/aibee, aibee_startup



edge_deploy/ABDMS/3559_dispatch

固件包含目录： aibee, abiee_startup

- aibee 目录包含（autoupdate,   k3s etc..）
- aibee_startup  启动autoupdate 目录，内含启动脚本



#### autoupdate 需注意事项

localupdate.cfg  : 需要添加初始version_num

```c
cat localupdate.cfg 
download_on_power = yes
download_period = 30
download_version_file_url = http://192.168.254.250:31080/version
download_version_file_url_backup= http://service.aibee.ipc:31080/version
k3s-agent_check_version_num = 0.0.8
AutoCameraConf_version_num = 0.0.1
TerminalServer_version_num = 0.0.1
```

##### version: 需要添加初始 启动项
```json
cat version
download_info=
[
  {
    "version_num": "0.0.1",
    "md5": "466ea75d3ea4db26eb8be4638c1ab4de",
    "update_time_point": "2019-05-15/15:41",
    "iplist": "((?:(?:25[0-5]|2[0-4][0-9]|((1[0-9]{2})|([1-9]?[0-9]))).){3}(?:25[0-5]|2[0-4][0-9]|((1[0-9]{2})|([1-9]?[0-9]))))",
    "download_excute_file_url": "http://service.aibee.ipc:31080/ternimal_server.tar",
    "execute_install_dir": "/dav/package/aibee/",
    "execute_name": "TerminalServer",
    "exe_dir_on_tar": "terminal_server",
    "exe_restart_shell": "start_terminal_server.sh",
    "kill_exe_and_no_daemon_flg": "no",
    "rm_exe_folder_flg": "no",
    "reboot_flg": "no"
  },
  {
    "version_num": "0.0.8",
    "md5": "466ea75d3ea4db26eb8be4638c1ab4de",
    "update_time_point": "2019-05-15/15:41",
    "iplist": "((?:(?:25[0-5]|2[0-4][0-9]|((1[0-9]{2})|([1-9]?[0-9]))).){3}(?:25[0-5]|2[0-4][0-9]|((1[0-9]{2})|([1-9]?[0-9]))))",
    "download_excute_file_url": "http://service.aibee.ipc:31080/k3s.tar",
    "execute_install_dir": "/dav/package/aibee/",
    "execute_name": "k3s-agent_check",
    "exe_dir_on_tar": "k3s-agent",
    "exe_restart_shell": "start_k3s.sh",
    "kill_exe_and_no_daemon_flg": "no",
    "rm_exe_folder_flg": "no",
    "reboot_flg": "yes"
  },
  {
    "version_num": "0.0.1",
    "md5": "466ea75d3ea4db26eb8be4638c1ab4de",
    "update_time_point": "2019-05-15/15:41",
    "iplist": "((?:(?:25[0-5]|2[0-4][0-9]|((1[0-9]{2})|([1-9]?[0-9]))).){3}(?:25[0-5]|2[0-4][0-9]|((1[0-9]{2})|([1-9]?[0-9]))))",
    "download_excute_file_url": "http://service.aibee.ipc:31080/face_auto_exposure.tar",
    "execute_install_dir": "/dav/package/aibee/",
    "execute_name": "AutoCameraConfig",
    "exe_dir_on_tar": "auto_camera_config",
    "exe_restart_shell": "startup.sh",
    "kill_exe_and_no_daemon_flg": "no",
    "rm_exe_folder_flg": "no",
    "reboot_flg": "no"
  }
]
```





#### minipc

1.  部署： nginx
2.  docker   -v  /kdj/data:/var/share/html/
3.  /kdj/data
   1.  version
   2.  要更新的tar 升级包
4.  注册 下载version url 地址 到 k-v 服务







## autoupdate

1. 如果md5sum 填错，会出现频繁下载，无法更新version
2. 如果url文件不存在，没有判断404









cp /dav/package/aibee/ABDMS/version   /dav/package/aibee/ABDMS/version_log

cp /dav/package/aibee/ABDMS/localupdate.cfg   /dav/package/aibee/ABDMS/localupdate.cfg_log

rm  cp /dav/package/aibee/ABDMS/version







```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: bodysdk64
  labels:
    name: bodysdk64
spec:
  selector:
    matchLabels:
      name: bodysdk64
  template:
    metadata:
      annotations:
        prometheus.io/scrape: "true"
        prometheus.io/port: "10011"
        prometheus.io/path: /metrics
      labels:
        name: bodysdk64
    spec:
      hostPID: true
      hostIPC: true
      hostNetwork: true
      nodeSelector:
        beta.kubernetes.io/arch: arm64
        kubernetes.io/hostname: 192.168.83.121
      tolerations:
      - effect: NoExecute
        operator: Exists
      - effect: NoSchedule
        operator: Exists
      initContainers:
      - command:
        - sh
        - -c
        - cp -r /root/svmodels/. /root/models/
        image: online-pipeline/modelmanage/svmodels_nnie_wanda_shanghai_bswd:1.0.0
        imagePullPolicy: IfNotPresent
        name: svmodel-init
        volumeMounts:
        - mountPath: /root/models
          name: model-vol
        workingDir: /root
      - command:
        - sh
        - -c
        - cp -r /root/svassets/. /root/body_assets/
        image: online-pipeline/assets/svassets_nnie_k11_guangzhou_artfull:1.0.0
        imagePullPolicy: IfNotPresent
        name: svassets-init
        volumeMounts:
        - mountPath: /root/body_assets
          name: assets-vol
        workingDir: /root
      - command:
        - sh
        - -c
        - cp -r /root/CameraInfos/. /root/camerainfos/ && cp -r /root/StoreInfos/. /root/storeinfos/
        image: online-pipeline/camerainfos/nnie_k11_guangzhou_artfull:1.0.0
        imagePullPolicy: IfNotPresent
        name: camerainfos-init
        volumeMounts:
        - mountPath: /root/camerainfos
          name: camerainfos-vol
        - mountPath: /root/storeinfos
          name: storeinfos-vol
        workingDir: /root
      containers:
      - image: edge/body_arm64:test.0.2
        imagePullPolicy: IfNotPresent
        name: bodysdk64
        ports:
          - containerPort: 10011
        resources:
          limits:
            cpu: 3200m
            memory: 2560Mi
          requests:
            cpu: 3000m
            memory: 2048Mi
        command:
          - sh
          - -c
          - sleep 1000h
          #- ./start_app.sh aegean_shanghai_wzl prod
        volumeMounts:
        - mountPath: /dev
          name: dev
        - mountPath: /var
          name: var
        - mountPath: /lib
          name: lib
        - mountPath: /mnt
          name: mnt
        - mountPath: /home
          name: home
        - mountPath: /root/models
          name: model-vol
        - mountPath: /root/body_assets
          name: assets-vol
        - mountPath: /root/CameraInfos
          name: camerainfos-vol
        - mountPath: /root/StoreInfos
          name: storeinfos-vol
        securityContext:
          privileged: true
      volumes:
        - name: dev
          hostPath:
            path: /dev
        - name: var
          hostPath:
            path: /var
        - name: lib
          hostPath:
            path: /lib
        - name: mnt
          hostPath:
            path: /mnt
        - name: home
          hostPath:
            path: /home
        - emptyDir: {}
          name: model-vol
        - emptyDir: {}
          name: assets-vol
        - emptyDir: {}
          name: camerainfos-vol
        - emptyDir: {}
          name: storeinfos-vol
```





~/body_front # ./prun.sh -d zhdc_foshan_hyc -p edge  -e test -n fid_nnie_0 -g 0,1
LD_LIBRARY_PATH: /root/usr/lib:/root/usr/lib/aarch64-linux-gnu:/root/usr/local/lib:/root/usr/lib/lapack:/root/usr/lib/libblas:/lib:/root/run/lib
PYTHONPATH: /root/usr/lib/python2.7
PATH: /opt/aibee/hadoop-2.6.5/bin:/bin:/usr/bin:/dav:/sbin:/usr/sbin:/root/usr/bin:/root/usr/local/bin:/root/usr/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
cfg_name: /root/body_assets/zhdc_foshan_hyc/zhdc_foshan_hyc.cfg
2020-05-25 20:17:15,126 INFO {'msg': 'loading files from /root/body_assets/zhdc_foshan_hyc/test/fid_nnie_0/unique.yaml'}
running zhdc_foshan_hyc/test/fid_nnie_0 with version 0.2.577
CUDA_VISIBLE_DEVICES=0,1
OMP_NUM_THREADS=1
/root/run/AibeeBody /root/body_assets/zhdc_foshan_hyc/test/base/fid_nnie /root/body_assets/zhdc_foshan_hyc/test/fid_nnie_0 test-edge -1





## sv debug



TimestampMeasureV2SEI::measure

TimestampMeasureV2::measure

TimestampMeasureV3OCR::measure

TimestampMeasureV3SEI::measure







1.  YUV        16:00:00        
2.  RTSP        16:00:00   
3.  YUV    5fps
4.  RTSP   25fps
3.   get_frame  -  YUV

          			   - RTSP



1. 描述

ABHAL(AiBee Hardware Abstraction Layer)硬件平台抽象层。目的统一各平台接口及尽最大可能使用硬件资源，也含一些基于芯片的优化等。

2. 现状

已实现功能：

- 3559，3519 硬件解码
- 3559，3519 格式转换，yuv2bgr, yuv2jpg,bgr2jpg...
- 3559, 3519  resize,  支持yvusp420, bgr-plannar

3. 接下来计划

适配x86,gpu 解码及相关格工转换功能。





4*3 = 12

4+2 = 3；



n*3/2