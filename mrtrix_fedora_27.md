
# MRtrix 3 installation in fedora

## 1. Install dependences

    dnf -y install git gcc-c++ python numpy eigen3-devel zlib-devel qt-devel mesa-libGL-devel

## 2. Install qt libraries

    dnf -y install qt* --skip-broken
    
Probably you'll have to export the environment variables for configuring the software

    export QMAKE=qmake-qt5
    export MOC=moc-qt5

## 3. Clone MRtrix repo
	git clone https://github.com/MRtrix3/mrtrix3.git

## 4. Configure the MRtrix3 install

    cd mrtrix3
	./configure

## 5. Build the binaries
	./build

## 6. Set path
	./set_path
