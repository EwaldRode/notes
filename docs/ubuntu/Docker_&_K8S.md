## docker 

### install docker
```bash
apt-get install docker.io -y
systemctl start docker
systemctl enable docker
```
### verify docker
```bash
docker --version
docker run hello-world
```

### fix docker permission errors
```bash
sudo groupadd docker
sudo usermod -aG docker $USER
``` 
--> reboot

## minikube 
### install minikube
```bash
wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
cp minikube-linux-amd64 /usr/local/bin/minikube
chmod 755 /usr/local/bin/minikube
```
### verify minikube
```bash
minikube version
```

## kubectl
### install kubectl
```bash
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | tee /etc/apt/sources.list.d/kubernetes.list
apt-get update -y
apt-get install kubectl kubeadm -y
```

### verify kubernetes
```bash
minikube start
kubectl cluster-info
kubectl config view
minikube status
```

### Kubernetes Dashboard
```bash
minikube dashboard --url
```

### Access minikube VM
```bash
minikube ssh
```