# Video codecs
```console
sudo dnf install gstreamer1-libav
```

# Python dependencies
It is important to have:
* Python devel (`python-dev` or `python-devel`)
* Pip

After installing those you must install the necessary dependencies using pip:
```console
pip3 install --user pandas numpy sklearn scikit-image requests matplotlib seaborn PySide2 dipy nibabel nilearn tables sqlalchemy
```
