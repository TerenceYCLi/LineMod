# LineMod
This is a Readme to install LindMod 6D pose recognition
Intsall Linemod

*** Please deactivate the conda environment first 
conda config --set auto_activate_base false
close and reopen shell to effective


# download and install opencv 4.5.0
# Install minimal prerequisites
sudo apt update && sudo apt install -y cmake g++ wget unzip
 
# Download and unpack sources
wget -O opencv-4.5.0.zip https://github.com/opencv/opencv/archive/refs/tags/4.5.0.zip
wget -O opencv_contrib-4.5.0.zip https://github.com/opencv/opencv_contrib/archive/refs/tags/4.5.0.zip
unzip opencv-4.5.0.zip
unzip opencv_contrib-4.5.0.zip
 
# Create build directory and switch into it
mkdir -p build && cd build
 
# Configure
# cmake -D OPENCV_EXTRA_MODULES_PATH=../opencv_contrib-4.5.0/modules ../opencv-4.5.0
cmake -D OPENCV_EXTRA_MODULES_PATH=../opencv_contrib-4.5.0/modules ../opencv-4.5.0 -D WITH_OPENMP=ON -D CMAKE_BUILD_TYPE=Release


# Build OpenCV
cmake --build .
# install
sudo make install

### Finish to install openCV


### Install LineMod
Github repo: https://github.com/aelmiger/LINE-MOD-Pipelines

# install dependency 
sudo apt-get install libglew-dev libglm-dev libassimp-dev libsdl2-dev

# get LINE-MOD code
git clone https://github.com/aelmiger/LINE-MOD-Pipeline.git LINE-MOD
cd LINE-MOD

# Install libfreenect2
git clone https://github.com/OpenKinect/libfreenect2.git
cd libfreenect2
sudo apt-get install build-essential cmake pkg-config
sudo apt-get install libusb-1.0-0-dev
sudo apt-get install libturbojpeg0-dev
sudo apt-get install libglfw3-dev

mkdir build && cd build
cmake .. -DCMAKE_INSTALL_PREFIX=$HOME/freenect2
make
make install

# Replace the CMakeList.txt in the LINE-MOD folder with 




# Build LineMod
cmake -H. -B build
cmake --build build --config Release --target all -- -j4

