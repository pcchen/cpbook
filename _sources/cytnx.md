# cytnx installations

## pip install
pip install . -vv

## Conda install

### OSX

#### python 3.8

````
conda create --channel conda-forge --name cytnx38 python=3.8 llvm-openmp
conda activate cytnx38
conda install -c kaihsinwu cytnx
````
## Build from source


### Ubuntu
**Prerequisites**

### MacOS (arm)+gcc+openblas
````
brew install gcc openblas lapack boost pybind11
````

````
cd /usr/local/lib
ln -s ../Cellar/openblas/0.3.20/lib/libopenblas.dylib
cd /usr/local/include
ln -s ../../Cellar/openblas/3.10.0/include/lapack*
````


### MacOS (Intel)+icpc+mkl
### MacOS (Intel)+gcc+mkl
### MacOS (Intel)+gcc+openblas

**Prerequisites**
* Install Homebrew.
* Use Homebrew to install following packages
````
brew install gcc openblas lapack boost pybind11
````

**Note**
* The openblas package does not provide `lapacke.h`. You have to install lapack package, which provide `lapacke.h`.
* Because homebrew installations of openblas/lapack are ot symbolic linked into /usr/local.
One way to fix this is to

````
cd /usr/local/lib
ln -s ../Cellar/openblas/0.3.20/lib/libopenblas.dylib
cd /usr/local/include
ln -s ../../Cellar/lapack/3.10.0/include/lapack*
````

**Build**
````
mkdir -p build
cd build
cmake -DCMAKE_C_COMPILER=/usr/local/bin/gcc-11 -DCMAKE_CXX_COMPILER=/usr/local/bin/g++-11 ..
````

### Raspberri Pi OS (64bit)
````
sudo apt update
sudo apt full-upgrade
sudo apt-get install cmake
sudo apt-get install libboost-all-dev
sudo apt-get install libopenblas-dev
sudo apt-get install libopenblas64-0 ??
sudo apt-get install liblapacke-dev
sudo apt-get install pybind11-dev
git clone https://github.com/Cytnx-dev/Cytnx.git

````
