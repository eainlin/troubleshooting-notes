# Linux Disk Management & EC2 Volume Expansion Guide
### Date: 11-Jun-2026
### Author: Htoo Eain Lin

## 1. Using `parted` to Check Free Space

```bash
sudo parted /dev/sda
print free
quit
```

## 2. Create New Partition with `fdisk`

```bash
fdisk /dev/sda
n               # new partition
Partition number: 4 (default)
First sector: <press Enter for default>
Last sector: <press Enter for default>
w               # write changes and quit
```

## 3. Extend LVM Volume

```bash
pvcreate /dev/sda4
vgextend ubuntu-vg /dev/sda4
lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```

## Fix Name Resolution Error

```bash
cat /etc/hostname
cat /etc/hosts
sudo systemctl restart systemd-resolved.service
sudo systemctl status systemd-resolved.service
```

## Extend Volumes in EC2 Instance

```bash
lsblk                     # check current disks and partitions
sudo growpart /dev/vda 1   # grow partition 1 on /dev/vda
lsblk                     # confirm new size
df -h                     # check filesystem size
sudo resize2fs /dev/vda1  # resize filesystem to use new partition space
df -h                     # verify expansion
```
