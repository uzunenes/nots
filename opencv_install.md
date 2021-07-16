# Opencv installation guide

## Create installation folder
```
$ mkdir opencv3415
$ cd opencv3415/
```

## Download opencv && opencv_contrib
```
$ wget https://github.com/opencv/opencv/archive/refs/tags/3.4.15.tar.gz
$ tar -xf 3.4.15.tar.gz 
$ wget https://github.com/opencv/opencv_contrib/archive/refs/tags/3.4.15.tar.gz
$ tar -xf 3.4.15.tar.gz.1
```

## Build opencv using Cmake
```
$ mkdir build
$ cd build/
```
>Warning: Install prerequisite libraries
```
$ cmake \
	-D CMAKE_BUILD_TYPE=RELEASE \
	-D CMAKE_INSTALL_PREFIX=/usr/local \
	-D INSTALL_PYTHON_EXAMPLES=ON \
	-D INSTALL_C_EXAMPLES=ON \
	-D WITH_TBB=ON \
	-D WITH_CUDA=ON \
	-D WITH_CUDNN=ON \
	-D OPENCV_DNN_CUDA=ON \
	-D BUILD_opencv_cudacodec=OFF \
	-D ENABLE_FAST_MATH=1 \
	-D CUDA_FAST_MATH=1 \
	-D WITH_CUBLAS=1 \
	-D WITH_QT=OFF \
	-D WITH_OPENGL=ON \
	-D WITH_GSTREAMER=ON \
	-D WITH_FFMPEG=ON \
	-D WITH_V4L=ON \
	-D WITH_LIBV4L=ON \
	-D OPENCV_GENERATE_PKGCONFIG=ON \
	-D BUILD_opencv_xfeatures2d=ON \
	-D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-3.4.15/modules \
	-D OPENCV_PC_FILE_NAME=opencv3415.pc \
	-D PYTHON_DEFAULT_EXECUTABLE=$(which python3) \
	-D BUILD_EXAMPLES=ON ..
```

## Make library
```
$ make -j100
```

## Install library
```
$ make install
```

## Test library
```
// test_opencv_library.cpp
#include <iostream>
#include <opencv2/opencv.hpp>

int
main()
{
	std::cout << cv::getBuildInformation() << "\n";
	
	return 0;
}
```

```
$ g++ -Wall test_opencv_library.cpp `pkg-config --cflags --libs opencv` -o test_opencv_library.out
$ ./test_opencv_library.out
```
