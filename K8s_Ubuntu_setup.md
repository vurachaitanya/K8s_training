# Installing K8s on Ubuntu 18.x

- apt-get update && apt-get install -y apt-transport-https
- curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -

- cat </etc/apt/sources.list.d/kubernetes.list

deb http://apt.kubernetes.io/ kubernetes-xenial main

EOF
- swapoff -a

- apt-get update
- apt-get install -y docker.io kubeadm kubectl kubelet kubernetes-cni
- systemctl enable docker
- systemctl start docker
- kubeadm init                                          

```

Your Kubernetes master has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

You can now join any number of machines by running the following on each node
as root:

  kubeadm join 10.0.2.15:6443 --token xxxxxxxxxxxxxxxx --discovery-token-ca-cert-hash sha256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

