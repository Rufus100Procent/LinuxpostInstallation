# Ubuntu Post Installation
# !/bin/bash 

sudo apt update;

sudo apt install nala -y;

#customization
sudo nala install gnome-shell-extension-manager -y;

sudo nala install gnome-shell-extensions -y;

sudo nala install gnome-tweaks -y;


#Installing flatbak
sudo nala update;
sudo nala install flatpak -y;
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo;

#install snap d
sudo apt-get install snapd -y

#Install Spotify
sudo nala update 
flatpak install flathub com.spotify.Client -y

#Install discord
sudo nala update 
flatpak install flathub com.discordapp.Discord -y

#Install Htop, Neofetch ....
sudo nala install htop -y
sudo nala install neofetch -y 
sudo nala install vim -y
sudo nala install vlc -y
sudo apt install bashtop

#install some SytemClean
sudo nala install stacer -y

#timshift/system backup
sudo nala update
sudo nala upgrade -y
sudo nala install timeshift -y 

#qemu/virtualization
sudo apt install glimpse
# to see if your system supports virtualization: type: agrep -c '(vmx|svm)' /proc/cpuinfo  (if it 0 you cant run virtualization)
#   LC_ALL=C lscpu | grep Virtualization 
sudo nala install qemu-kvm virt-manager bridge-utils -y 

#firefox
sudo snap remove firefox 

sudo add-apt-repository ppa:mozillateam/ppa
echo '
Package: *
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001
' | sudo tee /etc/apt/preferences.d/mozilla-firefox

echo 'Unattended-Upgrade::Allowed-Origins:: "LP-PPA-mozillateam:${distro_codename}";' | sudo tee /etc/apt/apt.conf.d/51unattended-upgrades-firefox

sudo nala update 

sudo nala install firefox -y

sudo apt-get install nvme-cli -y
#sudo nvme smart-log /dev/nvme0n1  

# Install Intelij Community
flatpak install flathub com.jetbrains.IntelliJ-IDEA-Community -y

# Zoom
flatpak install flathub us.zoom.Zoom -y


# Wine install
sudo dpkg --add-architecture i386 && sudo apt install wine
sudo ln -s /usr/share/doc/wine/examples/wine.desktop /usr/share/applications/
sudo mkdir -p /etc/apt/keyrings
wget -O - https://dl.winehq.org/wine-builds/winehq.key | gpg --dearmor | sudo tee /etc/apt/keyrings/winehq-archive.key
wget -nc https://dl.winehq.org/wine-builds/ubuntu/dists/$(lsb_release -sc)/winehq-$(lsb_release -sc).sources
sudo mv winehq-$(lsb_release -sc).sources /etc/apt/sources.list.d/
sudo apt update
sudo apt install winehq-staging

# games
flatpak install flathub org.supertuxproject.SuperTux -y

# optional
sudo apt install net-tools
sudo apt-get install ssh
sudo apt install cmake
udo apt install build-essential libssl-dev

#balenaEtcher
sudo nala install wget
wget https://github.com/balena-io/etcher/releases/download/v1.14.3/balenaEtcher-1.14.3-x64.AppImage

