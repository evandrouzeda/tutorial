# How to setup dev env on Linux manjaro

```
flatpak install flathub com.google.Chrome
```
```
flatpak override --user --filesystem=~/.local/share/applications --filesystem=~/.local/share/icons com.google.Chrome
```

## 1. Donwload and Install Docker
```
pamac install docker
```
```
sudo systemctl enable docker.service
```
```
sudo systemctl start docker.service
```
```
sudo groupadd docker
```
```
sudo usermod -aG docker $USER
```
```
newgrp docker
```
```
sudo reboot
```
## 2. Run docker container using the nodejs image and binding the the github folder
```
docker run -d -it --name devenv --mount type=bind,source=/home/$USER/GitHub/,target=/root --network host node
```
## 3. Download and install VsCode to attach to running container
```
sudo pacman -S snapd
```
```
sudo systemctl enable --now snapd.socket
```
```
sudo ln -s /var/lib/snapd/snap /snap
```
```
sudo snap install code --classic
```
## 4. Clone the repository to github folder after attach to running container
```
git clone url_to_repository
```
# Extras
## Reload Ollama connection with nvidia drives
```
#!/bin/bash
# First stop the service:
sudo systemctl stop ollama

# Reload nvidia_uvm:
sudo rmmod nvidia_uvm && sudo modprobe nvidia_uvm

# Then restart the service:
sudo systemctl start ollama
```
## Connect Nvidia to Docker
### 1. Install Nvidia Tookit
```
yay -Qs nvidia-container-toolkit
```
### 2. Configure Docker
```
sudo nvidia-ctk runtime configure --runtime=docker
```
### 3. Restart Docker
```
sudo systemctl restart docker
```
### 4. Test
```
docker run --rm --runtime=nvidia --gpus all ubuntu nvidia-smi
```
More in [Nvidia official guide](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)

## Create Python Container that uses Nvidia GPU
```
docker run -it --gpus all --runtime nvidia -v /home/$USER/GitHub/python/:/root -w /root --name pydev python:3.10 nvidia-smi
```
