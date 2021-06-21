#### A100 MIG

- Install nvidia driver from runfile : https://github.com/jear/nvidia-centos/blob/master/install.txt
 
- Install toolkit : https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#installing-on-centos-7-8

- Update 
```
vi /etc/docker/daemon.json

{
    "default-runtime": "nvidia",
    "runtimes": {
        "nvidia": {
            "path": "/usr/bin/nvidia-container-runtime",
            "runtimeArgs": []
        }
    }
}

pkill -SIGHUP dockerd
```

- Configure MIG without Slurm or k8s: https://github.com/jear/nvidia/blob/main/A100

- For k8s, look here : 
- https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/gpu-operator-mig.html#install-gpu-operator-mig
- https://github.com/jear/nvidia/blob/main/A100-k8s

- Add hosts in k8s GPU  cluster 

