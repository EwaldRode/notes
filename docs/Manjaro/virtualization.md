## update distro
```bash
sudo pacman -Syu
```

## install and setup libvirt + qemu 
```bash
sudo pacman -S --needed  virt-manager qemu-desktop libvirt edk2-ovmf dnsmasq libguestfs-tools libguestfs
```

sudo systemctl enable libvirtd.service
sudo systemctl start libvirtd.service
sudo usermod -aG libvirt ${USER}
sudo modprobe -r kvm_intel
sudo modprobe kvm_intel nested=1
echo "options kvm-intel nested=1" | sudo tee /etc/modprobe.d/kvm-intel.conf
systool -m kvm_intel -v | grep nested

qemu-img convert -o qcow2 metro-vm-disk1.vmdk metro-vm.qcow2
qemu-img convert -O qcow2 metro-vm-disk1.vmdk metro-vm.qcow2

qemu-img convert -O qcow2 Windows10Backup-disk1.vmdk Windows10Backup.qcow2
qemu-img convert -f vmdk -O qcow2 Windows10Backup-disk1.vmdk win10.qcow2

virt-install --name sit --ram 8192 --cpu host --os-variant win10 --vcpu 8 --disk /home/ewald/vms/win10/win10.qcow2,bus=ide --network bridge=virbr0 --import
virt-install --name sit --ram 8192 --cpu host --os-variant win10 --vcpu 8 --disk /home/ewald/vms/win10/win10.qcow2,bus=sata --network bridge=virbr0 --import
sudo pacman -S virt-what virt-image virt-top
mhwd-kernel -li

qemu-img convert -f vmdk -O qcow2 Windows10BackupVirtIO-disk1.vmdk Windows10BackupVirtIO.qcow2
sudo virsh net-start default

sudo pacman -Syu spice-vdaagent
sudo pacman -Syu spice-vdagent
systemctl enable spice-vdagent.service
systemctl enable spice-vdagentd.service

sudo virsh net-start default
xrandr
sudo mkdir /mnt/vfs_share
cd /mnt/vfs_share
sudo chown ewald:ewald /mnt/vfs_share
mkdir /mnt/vfs_share/git
ln -t /mnt/vfs_share/git sit
ln -t /mnt/vfs_share/git ~/sit
ln -s ~/sit /mnt/vfs_share/git
ln -s /mnt/vfs_share/git ~/dev/sit

sudo pacman -S docker
sudo pacman -S kubeadm 
docker run hello-world
docker info
sudo usermod -aG kvm $USER
sudo pacman -S gnome-terminal
systemctl --user start docker-desktop
systemctl --user start docker
systemctl enable docker
sudo systemctl start docker
sudo usermod -aG docker (user)
sudo usermod -aG docker ewald

sudo systemctl daemon-reload
sudo systemctl restart default-net-start.service
sudo systemctl status default-net-start.service