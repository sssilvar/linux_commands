# OpenCV Instalation in Fedora

We need CMake to configure the installation, GCC for compilation, Python-devel and Numpy for creating Python extensions etc.
<br>
<code>
dnf -y install cmake python-devel numpy gcc gcc-c++
</code>
<br>

Next we need GTK support for GUI features, Camera support (libdc1394, libv4l), Media Support (ffmpeg, gstreamer) etc.
<br>
<code>
dnf -y install gtk2-devel libdc1394-devel libv4l-devel ffmpeg-devel gstreamer-plugins-base-devel
</code>
<br>

Above dependencies are sufficient to install OpenCV in your fedora machine. But depending upon your requirements, you may need some extra dependencies. A list of such optional dependencies are given below. You can either leave it or install it, your call :)
<br>
OpenCV comes with supporting files for image formats like PNG, JPEG, JPEG2000, TIFF, WebP etc. But it may be a little old. If you want to get latest libraries, you can install development files for these formats.
<br>
<code>
dnf -y install libpng-devel libjpeg-turbo-devel jasper-devel openexr-devel libtiff-devel libwebp-devel
</code>
<br>
Several OpenCV functions are parallelized with Intel’s Threading Building Blocks (TBB). But if you want to enable it, you need to install TBB first. ( Also while configuring installation with CMake, don’t forget to pass -D WITH_TBB=ON. More details below.)
<br>
<code>
dnf -y install tbb-devel
</code>
<br>
Download OpenCV from Repo and create build folder
<br>
<code>
git clone https://github.com/Itseez/opencv.git

mkdir build
cd build
</code>
<br>
Now we have installed all the required dependencies, let’s install OpenCV. Installation has to be configured with CMake. It specifies which modules are to be installed, installation path, which additional libraries to be used, whether documentation and examples to be compiled etc. Below command is normally used for configuration (executed from build folder).
<br>
<code>
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_TBB=ON -D WITH_EIGEN=ON -D BUILD_DOCS=ON -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D BUILD_EXAMPLES=OFF -D WITH_OPENCL=OFF -D WITH_CUDA=OFF -D BUILD_opencv_gpu=OFF -D BUILD_opencv_gpuarithm=OFF -D BUILD_opencv_gpubgsegm=OFF -D BUILD_opencv_gpucodec=OFF -D BUILD_opencv_gpufeatures2d=OFF -D BUILD_opencv_gpufilters=OFF -D BUILD_opencv_gpuimgproc=OFF -D BUILD_opencv_gpulegacy=OFF -D BUILD_opencv_gpuoptflow=OFF -D BUILD_opencv_gpustereo=OFF -D BUILD_opencv_gpuwarping=OFF ..
</code>
<br>
Make and install (as su or sudo)
<br>
<code>
  make
  install

  su mv /usr/local/lib/python2.7/site-packages/cv2.so /usr/lib/python2.7/site-packages
</code>
