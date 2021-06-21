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

- Configure MIG, without Slurm or k8s: https://github.com/jear/nvidia/blob/main/A100

- For k8s, look here : 
- https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/gpu-operator-mig.html#install-gpu-operator-mig
- https://github.com/jear/nvidia/blob/main/A100-k8s

- Add hosts in k8s GPU  cluster 

- Reconfiguring MIG Profiles
The MIG manager supports dynamic reconfiguration of the MIG geometry. In this example, let’s reconfigure the GPU into a 3g.20gb profile:
```
kubectl label nodes $NODE nvidia.com/mig.config=all-3g.20gb --overwrite
```

- Telemetry (DCGM in k8s)
- https://docs.nvidia.com/datacenter/cloud-native/kubernetes/dcgme2e.html
