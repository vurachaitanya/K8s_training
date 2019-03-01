#

- apt-get update && apt-get install -y apt-transport-https
- curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -

- cat </etc/apt/sources.list.d/kubernetes.list
deb http://apt.kubernetes.io/ kubernetes-xenial main
EOF

- cat </etc/apt/sources.list.d/kubernetes.list
deb http://apt.kubernetes.io/ kubernetes-xenial main
EOF

- apt-get update
- apt-get install -y docker.io kubeadm kubectl kubelet kubernetes-cni
- apt-get install -y docker.io kubeadm kubectl kubelet kubernetes-cni
- kubeadm init                                          

Your Kubernetes master has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

- mkdir -p $HOME/.kube
-  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
-  sudo chown $(id -u):$(id -g) $HOME/.kube/config
