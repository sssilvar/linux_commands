# Some important thiing about Docker
## Docker in fedora 31
You may need a correction in the grub file using:

```bash
sudo dnf install grubby
sudo grubby --update-kernel=ALL --args="systemd.unified_cgroup_hierarchy=0"
```

# Bug in Docker + Fedora 31
Bug: `docker: Error response from daemon: cgroups: cgroup mountpoint does not exist: unknown.`

Solution
```bash
sudo mkdir /sys/fs/cgroup/systemd
sudo mount -t cgroup -o none,name=systemd cgroup /sys/fs/cgroup/systemd
```

# Docker out of space
Move the image default directory to a partition/folder with more space:
```bash
sudo service docker stop
sudo mv /var/lib/docker /new_path/docker
sudo ln -s /new_path/docker /var/lib/docker  # Creates link
service docker start
```