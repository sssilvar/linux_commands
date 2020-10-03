# Making your DSLR a webcam
Source: https://medium.com/nerdery/dslr-webcam-setup-for-linux-9b6d1b79ae22 


## Install dependencies
```bash
sudo dnf install gphoto2 ffmpeg
```

To install `v4l2loopback`:
```bash
sudo dnf copr enable sentry/v4l2loopback
sudo dnf install v4l2loopback
```

Start the webcam device with:
```bash
gphoto2 --stdout --capture-movie | ffmpeg -i - -vcodec rawvideo -pix_fmt yuv420p -threads 0 -f v4l2 /dev/video4
```
