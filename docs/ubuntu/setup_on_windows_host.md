# Setup ubuntu VM with Windows Host
this repository provides the user with solutions to update a development distro

## hyper-v 
Generation 2 UEFI VM
deactivate secure boot
Guest Sessions aktivieren
increase RAM + CPU Count

If needed, execute ./install.sh twice
```bash
wget https://raw.githubusercontent.com/Microsoft/linux-vm-tools/master/ubuntu/18.04/install.sh
sudo chmod +x install.sh
sudo ./install.sh
```
Falls Fehler auftreten. /etc/xrdp/xrdp.ini editieren
```bash
port=vsock://-1:3389
use_vsock=false
```

Dependency installieren:
```bash
sudo apt-get install xorgxrdp-hwe-18.04
```

VM stoppen und in Powershell(Admin):
```bash
Set-VM -VMName <your_vm_name>  -EnhancedSessionTransportType HvSocket
```

## change ubuntu vm resolution
```bash
sudo nano /etc/default/grub
```
Find GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Append that line with video=hyperv_fb:[specify resolution, e.g. 1024x768]
```bash
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=hyperv_fb:1024x768"
```
Save changes and exit
```bash
sudo update-grub
```
Restart the VM

## update distro
```bash
sudo apt-get update -y
sudo apt-get dist-upgrade -y
sudo apt-get upgrade -y
sudo apt autoremove -y
```

## common tools
```bash
sudo apt-get install curl wget apt-transport-https -y
```