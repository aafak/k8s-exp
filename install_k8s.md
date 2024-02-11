https://www.linuxbuzz.com/install-minikube-on-ubuntu/

aafak@aafak-virtual-machine:~/k8s_install$ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 89.3M  100 89.3M    0     0  8167k      0  0:00:11  0:00:11 --:--:-- 10.8M
aafak@aafak-virtual-machine:~/k8s_install$


aafak@aafak-virtual-machine:~/k8s_install$ sudo install minikube-linux-amd64 /usr/local/bin/minikube
[sudo] password for aafak:
aafak@aafak-virtual-machine:~/k8s_install$

aafak@aafak-virtual-machine:~/k8s_install$ minikube version
minikube version: v1.32.0
commit: 8220a6eb95f0a4d75f7f2d7b14cef975f050512d
aafak@aafak-virtual-machine:~/k8s_install$


aafak@aafak-virtual-machine:~/k8s_install$ curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 47.4M  100 47.4M    0     0  7829k      0  0:00:06  0:00:06 --:--:-- 10.2M
aafak@aafak-virtual-machine:~/k8s_install$

aafak@aafak-virtual-machine:~/k8s_install$ chmod +x kubectl
aafak@aafak-virtual-machine:~/k8s_install$ sudo mv kubectl /usr/local/bin/
aafak@aafak-virtual-machine:~/k8s_install$ kubectl version -o yaml
clientVersion:
  buildDate: "2024-01-17T15:51:03Z"
  compiler: gc
  gitCommit: bc401b91f2782410b3fb3f9acf43a995c4de90d2
  gitTreeState: clean
  gitVersion: v1.29.1
  goVersion: go1.21.6
  major: "1"
  minor: "29"
  platform: linux/amd64
kustomizeVersion: v5.0.4-0.20230601165947-6ce0bf390ce3

The connection to the server localhost:8080 was refused - did you specify the right host or port?
aafak@aafak-virtual-machine:~/k8s_install$

aafak@aafak-virtual-machine:~/k8s_install$ minikube start --driver=docker
* minikube v1.32.0 on Ubuntu 22.04
* Using the docker driver based on user configuration
* Using Docker driver with root privileges
* Starting control plane node minikube in cluster minikube
* Pulling base image ...
* Downloading Kubernetes v1.28.3 preload ...
    > gcr.io/k8s-minikube/kicbase...:  453.90 MiB / 453.90 MiB  100.00% 6.74 Mi
    > preloaded-images-k8s-v18-v1...:  403.35 MiB / 403.35 MiB  100.00% 5.16 Mi
* Creating docker container (CPUs=2, Memory=2200MB) ...
* Preparing Kubernetes v1.28.3 on Docker 24.0.7 ...
  - Generating certificates and keys ...
  - Booting up control plane ...
  - Configuring RBAC rules ...
* Configuring bridge CNI (Container Networking Interface) ...
  - Using image gcr.io/k8s-minikube/storage-provisioner:v5
* Verifying Kubernetes components...
* Enabled addons: storage-provisioner, default-storageclass
* Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
aafak@aafak-virtual-machine:~/k8s_install$

aafak@aafak-virtual-machine:~/k8s_install$ minikube status
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured

aafak@aafak-virtual-machine:~/k8s_install$

aafak@aafak-virtual-machine:~/k8s_install$ kubectl get nodes
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   87s   v1.28.3
aafak@aafak-virtual-machine:~/k8s_install$ kubectl get pods
No resources found in default namespace.
aafak@aafak-virtual-machine:~/k8s_install$


aafak@aafak-virtual-machine:~/k8s_install$ kubectl cluster-info
Kubernetes control plane is running at https://192.168.49.2:8443
CoreDNS is running at https://192.168.49.2:8443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
aafak@aafak-virtual-machine:~/k8s_install$

aafak@aafak-virtual-machine:~/k8s_install$ kubectl get svc
NAME         TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   2m53s
aafak@aafak-virtual-machine:~/k8s_install$
