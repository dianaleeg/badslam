How to Setup BADSLAM on Ubuntu Linux:

-- Beware, there are many packages to install and many kinks to resolve along the way bc ~software. 

1. Install BOOST

 - https://www.boost.org/

 $ sudo apt-get install libboost-all-dev

2. Install CUDA
 
 Follow these detailed instructions: https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html

3. Install DLib

- DLib, not dlib - everyone under the sun has spent too much debugging issues related to dlib when all you really needed was DLib: https://github.com/dorian3d/DLib 

 $ git clone https://github.com/dorian3d/DLib.git
 $ cd DLib
 $ mkdir build
 $ cd build
 $ cmake ..
 $ make
 $ make install

4. Install Eigen

 - http://eigen.tuxfamily.org/index.php?title=Main_Page

 $ git clone https://gitlab.com/libeigen/eigen.git
 $ cd eigen
 $ mkdir build
 $ cd build
 $ cmake ..
 $ make
 $ make install

5. Install g2o

 $ git clone https://github.com/RainerKuemmerle/g2o.git
 $ cd g2o 
 $ mkdir build
 $ cd build
 $ cmake ..
 $ make
 $ make install

6. Install GLEW

 - http://glew.sourceforge.net/build.html

 $ sudo apt-get install libXmu-dev libXi-dev libgl-dev dos2unix git wget

7. Install GoogleTest (GTest)

 $ git clone https://github.com/google/googletest.git
 $ cd googletest
 $ mkdir build
 $ cd build
 $ cmake ..
 $ make
 $ make install

8. Install OpenCV 3.X
 
 - Follow these instructions: https://learnopencv.com/install-opencv3-on-ubuntu/

9. Install OpenGV 

 $ git clone https://github.com/laurentkneip/opengv.git
 $ cd opengv
 $ mkdir build
 $ cd build
 $ cmake ..
 $ make
 $ make install

10. Install Qt

 $ git clone git://code.qt.io/qt/qt5.git
 $ cd qt5
 $ git checkout 5.12
 $ mkdir build
 $ cd build
 $ cmake ..
 $ make
 $ make install

11. Install SuiteSparse

 $ sudo apt install libsuitesparse-dev

12. Install Zlib

 https://sourceforge.net/projects/libpng/files/zlib/1.2.11/zlib-1.2.11.tar.gz/download?use_mirror=pilotfiber&download=

DONE WITH REQUIRED DEPENDENCIES -- BUT - I DO RECOMMEND INSTALLING THE OPTIONAL PACKAGES BC ERRORS WILL OCCUR AND ARE ANNOYING WHEN YOU TRY TO FILTER WHATS GOING WELL/WHAT ISN'T!

1. Install RealSense

 $ git clone https://github.com/IntelRealSense/librealsense.git
 $ cd librealsense
 $ mkdir build
 $ cd build
 $ cmake ..
 $ make
 $ make install

2. Install Structure

 Go to : https://developer.structure.io/portal
 Click 'Download Structure SDK (Cross-Platform)'

 Oonce downloaded, unzip!

 $ cd Structure
 $ mkdir build
 $ cd build
 $ cmake ..
 $ make
 $ make install

3. Install Azure Kinect SDK

 $ git clone https://github.com/microsoft/Azure-Kinect-Sensor-SDK.git

 Before proceeding, this SDK has many dependencies, so kind of a rabbit hole of other things to download and install:
 Azure Build Instructions:https://github.com/microsoft/Azure-Kinect-Sensor-SDK/blob/develop/docs/building.md

 Follow instructions on where to create build files and how to run!

ALL PACKAGES INSTALLED!

Moment of truth, build BADSLAM:

1. Inside of badslam
 $ mkdir build_RelWithDebInfo
 $ cd build_RelWithDebInfo
 $ cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo -DCMAKE_CUDA_FLAGS="-arch=sm_61" ..
 $ make -j badslam  # Reduce the number of threads if running out of memory, e.g., -j3
