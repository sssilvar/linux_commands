# Setup flatpak using terminal
First, it is necessary to have Flatpak installed. In Fedora, this is done as follows:
```bash
dnf install flatpak
```

Then, you need to add the flathub repository:
```bash
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
