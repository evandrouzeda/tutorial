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
flatpak run com.visualstudio.code
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
