# Automation setup 1-master k8s cluster with external etcd cluster (only debian)

## Requirement

1. Minimum 5 **nodes** [One master, one worker node and three etcd nodes]. You can have more worker nodes as per your requirement.
2. The master node should have a minimum of **2 vCPU and 2GB RAM**.
3. For the worker nodes, a minimum of 1vCPU and 2 GB RAM is recommended.
4. 192.X.X.X/X network range with static IPs for master and worker nodes. We will be using the 10 series as the pod network range that will be used by the Calico network plugin. Make sure the Node IP range and pod IP range don’t overlap.
5. Internet connectivity for pulling containers required (Private registry can also be used)
6. Full network connectivity between machines in the cluster – This is private or public

### Ports

- master:

  - kube-scheduler: 10251
  - kube-controller-manager: 10252
  - kubelet: 10250
  - api server: 6443

- workers:

  - api server: 6443

- etcd: 2379, 2380

## Support:

- OS: debian
- network: calico, flannel
- etcd deployment: kubeadm, service (systemd)

## Notes

- **Please read through global var file in: ./host_vars/all.yml**
- **If want clear k8s n etcd cluster, run playbooks: reset-etcd-cluster.yml, reset-k8s.yml**

> manual setup: https://dangquang.notion.site/Install-k8s-cluster-using-kubeadm-c3528ceddd9a48d2b308dbd822348273
