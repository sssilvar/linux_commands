# Recommended commands for Web development
## Photo scaling
To scale a bunch of photos go to the target folder and type:

    find . -maxdepth 1 -iname "*.jpg" | xargs -L1 -I{} convert -resize 25% "{}" _resized/"{}"

## Photo orientation
To make HTML detect the right orientation of the pictures:

    jhead -autorot *.JPG
