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
#Docker history commands
````
 sudo su -
    2  mkdir -p $HOME/.kube
    3  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
    4  sudo chown $(id -u):$(id -g) $HOME/.kube/config
    5  kubectl getnodes
    6  kubectl get nodes
    7  kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
    8  kubectl get nodes
    9  kubectl get ns
   10  kubectl
   11  kubectl get pods --show-all
   12  kubectl get pods --help
   13  kubectl get pods --all-namespaces
   14  kubectl get ds
   15  kubectl get deployments
   16  kubectl get rc
   17  kubectl get ns
   18  kubectl get pods --all-namespaces -o wide
   19   kubectl get pods -n kube-system
   20  kubectl describe etcd-ip-172-31-28-38.ap-south-1.compute.internal
   21  kubectl describe etcd-ip-172-31-28-38.ap-south-1.compute.internal -n kube-system
   22  kubectl describe pods etcd-ip-172-31-28-38.ap-south-1.compute.internal -n kube-system
   23  kubectl describe pods etcd-ip-172-31-28-38.ap-south-1.compute.internal -n kube-system --json
   24  kubectl describe pods etcd-ip-172-31-28-38.ap-south-1.compute.internal -n kube-system -o json
   25  kubectl describe pods etcd-ip-172-31-28-38.ap-south-1.compute.internal -n kube-system --show-events=true
   26  docker get secureity
   27  kubectl get  apiservices
   28  kubectl get  apiservices|grep metri
   29  kubectl get  apiservices|grep metrics
   30  kubectl create ns chaitu_ns
   31  kubectl create namespace chaitu-ns
   32  pods/resource/memory-request-limit.yaml
   33  apiVersion: v1
   34  kind: Pod
   35  metadata:
   36    name: memory-demo
   37    namespace: mem-example
   38  spec:
   39    containers:
   40    - name: memory-demo-ctr
   41      image: polinux/stress
   42      resources:
   43        limits:
   44          memory: "200Mi"
   45        requests:
   46          memory: "100Mi"
   47      command: ["stress"]
   48      args: ["--vm", "1", "--vm-bytes", "150M", "--vm-hang", "1"]
   49  vi memory_request_limits.yaml
   50  kubectl create pod -f memory_request_limits.yaml -n chaitu-ns
   51  kubectl create -h
   52  kubectl create -f memory_request_limits.yaml -n chaitu-ns
   53  kubectl get pods -n chaitu-ns
   54  kubectl describe chaitu-ns -n chaitu-ns
   55  kubectl describe pod chaitu-ns -n chaitu-ns
   56  kubctl status
   57  kubectl
   58  kubectl  top
   59  kubectl  top pods
   60  kubectl  top pods -n chaitu-ns
   61  kubectl  top nodes
   62  kubectl  top node
   63  kubectl top pods chaitu-ns
   64  kubctl get services heapster
   65  kubectl get services heapster
   66  kubectl get services http:heapster
   67  kubectl get services
   68  kubectl describe pod chaitu-ns --output=yaml -n chaitu-ns
   69  kubectl get  pod chaitu-ns --output=yaml -n chaitu-ns
   70  kubectl top pod chaitu-ns --namespace=chaitu-ns
   71  kubectl get pods -n kube-system
   72  kubectl get pods --all-namespaces
   73  kubectl top node --heapster-namespace='default
````
