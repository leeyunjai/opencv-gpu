# opencv-gpu
opencv gpu compile

# install
sudo apt-get update -y  
#sudo apt-get upgrade  
sudo apt-get install build-essential cmake unzip pkg-config -y  
sudo apt-get install libjpeg-dev libpng-dev libtiff-dev -y  
sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev -y  
sudo apt-get install libv4l-dev libxvidcore-dev libx264-dev -y  
sudo apt-get install libgtk-3-dev -y  
sudo apt-get install libatlas-base-dev gfortran -y  
sudo apt-get install python3-dev -y  

wget -O opencv.zip https://github.com/opencv/opencv/archive/4.2.0.zip  
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.2.0.zip  
unzip opencv.zip  
unzip opencv_contrib.zip  
mv opencv-4.2.0 opencv  
mv opencv_contrib-4.2.0 opencv_contrib  

cd opencv  
mkdir build  
cd build  

# CUDA_ARCH_BIN (1080Ti -> 6.1)  

cmake -D CMAKE_BUILD_TYPE=RELEASE \  
        -D CMAKE_INSTALL_PREFIX=/usr/local \  
        -D INSTALL_PYTHON_EXAMPLES=ON \  
        -D INSTALL_C_EXAMPLES=OFF \  
        -D OPENCV_ENABLE_NONFREE=ON \  
        -D WITH_CUDA=ON \  
        -D WITH_CUDNN=ON \  
        -D OPENCV_DNN_CUDA=ON \  
        -D ENABLE_FAST_MATH=1 \  
        -D CUDA_FAST_MATH=1 \  
        -D CUDA_ARCH_BIN=6.1 \  
        -D WITH_CUBLAS=1 \  
        -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \  
        -D HAVE_opencv_python3=ON \  
        -D PYTHON_EXECUTABLE=/usr/bin/python \  
        -D BUILD_EXAMPLES=ON ..  
make
sudo make install
sudo ldconfig
