**Author**: Alessandro Giudice

# GROMACS for beginners

This guide is for `GROMACS 2022.3` version. For the next versions, you must change version number in the latest installation guide.  
https://manual.gromacs.org/documentation/current/install-guide/index.html  

If you want some tutorials:  
http://www.mdtutorials.com/gmx/  

If you have a CUDA enabled GPU:  
https://www.nvidia.com/en-sg/data-center/gpu-accelerated-applications/gromacs/

## Dependencies
### Compilers and CMake
```
sudo apt-get -y install build-essential cmake
```
### Python 
```
python3 -m pip install --upgrade pip cmake scikit-build
```

## Install 
https://manual.gromacs.org/documentation/#latest-releases   
Full instructions are
```
wget https://ftp.gromacs.org/gromacs/gromacs-2022.3.tar.gz
tar xfz gromacs-2022.3.tar.gz
cd gromacs-2022.3
mkdir build
cd build
cmake .. -DGMX_BUILD_OWN_FFTW=ON -DREGRESSIONTEST_DOWNLOAD=ON
make -j 4
make -j 4 check
sudo make install
cd
rm gromacs-2022.3.tar.gz
rm -rf gromacs-2022.3
```
NOTE: If your system support more of 4 jobs, you can change -j option value.  
Checking your installation and using GROMACS:  
```
source /usr/local/gromacs/bin/GMXRC
gmx
```
## Install gmxapi  
To use GROMACS with Python  
https://manual.gromacs.org/current/gmxapi/userguide/install.html
```
python3 -m pip install --upgrade cmake scikit-build gmxapi
```
## Uninstall
It is sufficient to delete the relative folder
```
cd /usr/local/
sudo rm -rf gromacs
```
then remove the GROMACS's environment variable and uninstall `gmxapi` pip package.
