---
layout: post
---

# Managing Virtual Machines with libvirt:

## Installing:
```
sudo apt update
sudo apt install qemu-kvm libvirt-daemon-system
sudo adduser $USER libvirt
```

## Management commands:
- List running VMs
```
virsh list
```
- Start commands:
```
virsh start <guestname>
virsh autostart <guestname> #start at boot
virsh reboot
virsh save <guestname> <name>.state #save the current state of a VM
virsh restore <name>.state #To restore a VM
virsh shutdown <guestname>
virsh attach-disk <guestname> /dev/cdrom /media/cdrom #to attach a CD-ROM

```
