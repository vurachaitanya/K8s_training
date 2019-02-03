# K8s_training
K8s Training from Rajesh on 2nd Feb 2019.
palmetto training center
- https://www.devopsschool.com/notes/kubernetes/
- https://www.devopsschool.com/notes/docker/2019/online-jan-2019.txt
- https://www.devopsschool.com/tutorial/docker/
- https://www.devopsschool.com/pdf/docker/
- https://www.devopsschool.com/slides/docker/
- https://www.devopsschool.com/slides/kubernetes/getting-started-kubernetes/#/22
- Docker links ---linking dockers
- Cluster store ----k8s database etc
- Types of container:
    Rocket
    Crio container
    Cryod
    Containerd
 - https://medium.com/@pmvk/tips-to-crack-certified-kubernetes-administrator-cka-exam-c949c7a9bea1
 - Networking : https://ahmet.im/blog/kubernetes-network-policy/
 - Certificates : https://brancz.com/2017/10/16/kubernetes-auth-x509-client-certificates/

````
sudo yum install -y yum-utils device-mapper-persistent-data lvm2 -y 
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum install –y https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm -y
yum-config-manager --enable rhui-REGION-rhel-server-extras
yum install -y docker-ce
systemctl enable docker
systemctl start docker

cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
exclude=kube*
EOF

setenforce 0
sed -i 's/^SELINUX=enforcing$/SELINUX=permissive/' /etc/selinux/config

yum install -y kubelet kubeadm kubectl --disableexcludes=kubernetes

systemctl enable --now kubelet

==============
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

  kubeadm join 172.31.28.38:6443 --token 8063lq.ychn6q57adi0mdu2 --discovery-token-ca-cert-hash sha256:44ca37c0ca90a9bafbdb416d910902bc312fb4ca0ae92e91d000c94dbcbc1340

================================
  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config


kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"

````
