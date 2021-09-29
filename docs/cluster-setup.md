# How to init the k8s cluster

## Install updates
```shell
sudo apt update && \
sudo apt -y upgrade && sudo systemctl reboot
```

## Install kubeadm
```shell
# Install docker
sudo apt-get update && \
sudo apt-get -y install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release && \
(curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg) && \
(echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null) && \
sudo apt-get update && \
sudo apt-get -y install docker-ce docker-ce-cli containerd.io && \
{ sudo tee /etc/docker/daemon.json <<-EOF
{
  "exec-opts": ["native.cgroupdriver=systemd"],
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "100m"
  },
  "storage-driver": "overlay2"
}
EOF
} && sudo usermod -aG docker $USER && \

# Install kubeadm
(curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -) && \
(echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list) && \
sudo apt update && \
sudo apt -y install kubelet kubeadm kubectl && \
sudo apt-mark hold kubelet kubeadm kubectl && \

# Disable swap
sudo sed -i '/swap/ s/^\(.*\)$/#\1/g' /etc/fstab && \
sudo swapoff -a
```
