# Build a Kubernetes cluster using k3s via Ansible

Author: <https://github.com/itwars>

## K3s Ansible Playbook

Build a Kubernetes cluster using Ansible with k3s. The goal is easily install a Kubernetes cluster on machines running:

- [X] Debian
- [X] Ubuntu
- [X] CentOS

on processor architecture:

- [X] x64
- [X] arm64
- [X] armhf

## System requirements

Deployment environment must have Ansible 2.4.0+
Master and nodes must have passwordless SSH access

## Usage


If needed, you can also edit `inventory/rpi-cluster/group_vars/all.yml` to match your environment.

Start provisioning of the cluster using the following command:

```bash
$ ansible-playbook site.yml -i inventory/rpi-cluster/hosts.ini
```

## Kubeconfig

To get access to your **Kubernetes** cluster just

```bash
$ scp pi@192.168.0.119:~/.kube/config ~/.kube/config
```

View nodes:

```
$ kubectl get nodes --output wide
NAME     STATUS   ROLES    AGE     VERSION        INTERNAL-IP     EXTERNAL-IP   OS-IMAGE                         KERNEL-VERSION   CONTAINER-RUNTIME
rpi-07   Ready    <none>   7m18s   v1.18.9+k3s1   192.168.0.121   <none>        Raspbian GNU/Linux 10 (buster)   5.4.51-v7l+      containerd://1.3.3-k3s2
rpi-05   Ready    master   7m44s   v1.18.9+k3s1   192.168.0.119   <none>        Raspbian GNU/Linux 10 (buster)   5.4.51-v7l+      containerd://1.3.3-k3s2
rpi-02   Ready    <none>   6m53s   v1.18.9+k3s1   192.168.0.116   <none>        Raspbian GNU/Linux 10 (buster)   5.4.51-v7+       containerd://1.3.3-k3s2
rpi-03   Ready    <none>   6m50s   v1.18.9+k3s1   192.168.0.117   <none>        Raspbian GNU/Linux 10 (buster)   5.4.51-v7+       containerd://1.3.3-k3s2
rpi-06   Ready    <none>   7m17s   v1.18.9+k3s1   192.168.0.120   <none>        Raspbian GNU/Linux 10 (buster)   5.4.51-v7l+      containerd://1.3.3-k3s2
rpi-01   Ready    <none>   6m46s   v1.18.9+k3s1   192.168.0.115   <none>        Raspbian GNU/Linux 10 (buster)   5.4.51-v7+       containerd://1.3.3-k3s2
```
