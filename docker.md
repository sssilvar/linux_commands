# Some important things about Docker

## Docker compose
Check the installation guide here: https://docs.docker.com/compose/install/ 
For linux:
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

## Docker in fedora 31
You may need a correction in the grub file using:

```bash
sudo dnf install grubby
sudo grubby --update-kernel=ALL --args="systemd.unified_cgroup_hierarchy=0"
```

# Bug in Docker + Fedora 31
Bug: `docker: Error response from daemon: cgroups: cgroup mountpoint does not exist: unknown.`

### temporary solution
```bash
sudo mkdir /sys/fs/cgroup/systemd
sudo mount -t cgroup -o none,name=systemd cgroup /sys/fs/cgroup/systemd
```

### Permanent solution (a bit riskier)
```bash
sudo vi /etc/default/grub
```

Make this like look kie this (the important part is `systemd.unified_cgroup_hierarchy=0`):
```bash
GRUB_CMDLINE_LINUX=" rd.luks.uuid=luks-a99d782d-56f0-46cf-9ff0-0ae91f0963c9 rd.lvm.lv=system/root rd.lvm.lv=system/swap biosdevname=0 net.ifnames=0 resume=/dev/disk/by-uuid/34631ce6-b93e-4cb0-8cf5-72aada118b97 rhgb systemd.unified_cgroup_hierarchy=0 quiet"
```

and rebuild the grub:
```bash
# if using UEFI
sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
# or if using BIOS
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```

# Docker out of space
Move the image default directory to a partition/folder with more space:
```bash
sudo service docker stop
sudo mv /var/lib/docker /new_path/docker
sudo ln -s /new_path/docker /var/lib/docker  # Creates link
service docker start
```

# Clean slate (delete all the images and containers)
```bash
docker system prune
```
