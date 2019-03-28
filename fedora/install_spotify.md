First, it is necessary to install the RPM fussion. 
After that, you just need to execute:

```
sudo dnf install lpf-spotify-client
lpf approve spotify-client
sudo -u pkg-build lpf build spotify-client 
sudo dnf install /var/lib/lpf/rpms/spotify-client/spotify-client-*.rpm
```
