- ```shell
  
  docker manifest create private-registry.aibee.cn:5000/advertise/pause:3.1 private-registry.aibee.cn:5000/advertise/pause:3.1-arm private-registry.aibee.cn:5000/advertise/pause:3.1-arm64 private-registry.aibee.cn:5000/advertise/pause:3.1-amd64 --amend --insecure
  
  
  docker manifest annotate --arch=arm --os=linux --variant=v7  private-registry.aibee.cn:5000/advertise/pause:3.1 private-registry.aibee.cn:5000/advertise/pause:3.1-arm
  
  docker manifest annotate --arch=arm64 --os=linux --variant=v8 private-registry.aibee.cn:5000/advertise/pause:3.1 registry.aibee.cn:5000/advertise/pause:3.1-arm64
  
  
  docker manifest annotate --arch=amd64 --os=linux private-registry.aibee.cn:5000/advertise/pause:3.1 registry.aibee.cn:5000/advertise/pause:3.1-amd64
  
  docker manifest push --insecure private-registry.aibee.cn:5000/advertise/pause:3.1 
  
  docker tag private-registry.aibee.cn:5000/advertise/pause:3.1 https://private-registry.aibee.cn:5000/advertise/pause:3.1
  
  
  docker 
  
  ```

  