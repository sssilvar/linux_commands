# Some important thiing about Docker
## Docker in fedora 31
You may need a correction in the grub file using:

```bash
sudo dnf install grubby
sudo grubby --update-kernel=ALL --args="systemd.unified_cgroup_hierarchy=0"
```
