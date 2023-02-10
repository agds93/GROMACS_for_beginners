**Author**: Alessandro Giudice  

<a href="https://www.paypal.com/donate/?hosted_button_id=WWSJK522GMUVC">
<img alt="" src="https://raw.githubusercontent.com/agds93/GROMACS_for_beginners/main/img/Paypal.png" width="175" height="auto">
</a>

# [GROMACS](https://www.gromacs.org/) for beginners
This guide is for `GROMACS 2023` version. For the next versions, you must change version number in the instructions.  
The typical version name is `GROMACS year.number`, where `year` is the year of the major release and `number` is the number of the minor release. For example `GROMACS 2022.4` is the fourth minor release of the 2022 version. The minor updates can continue even after the release year.

## Documentation
GROMACS's official installation guide (a simpler one is below):  
[https://manual.gromacs.org/documentation/current/install-guide/index.html](https://manual.gromacs.org/documentation/current/install-guide/index.html)  

GROMACS releases:  
[https://manual.gromacs.org/documentation/#latest-releases](https://manual.gromacs.org/documentation/#latest-releases)
[https://manual.gromacs.org/documentation/current/download.html](https://manual.gromacs.org/documentation/current/download.html)
[https://manual.gromacs.org/current/release-notes/index.html](https://manual.gromacs.org/current/release-notes/index.html)

GROMACS tutorials:  
[https://tutorials.gromacs.org/md-intro-tutorial.html](https://tutorials.gromacs.org/md-intro-tutorial.html) 
[https://manual.gromacs.org/current/user-guide/index.html](https://manual.gromacs.org/current/user-guide/index.html)  
[http://www.mdtutorials.com/gmx/](http://www.mdtutorials.com/gmx/)  

gmxapi:   
[https://manual.gromacs.org/current/gmxapi/userguide/install.html](https://manual.gromacs.org/current/gmxapi/userguide/install.html)

CUDA GPUs:  
[https://developer.nvidia.com/cuda-gpus](https://developer.nvidia.com/cuda-gpus)

## Ubuntu and its derivatives (e.g. Linux Mint)

### Dependencies
#### Compilers and CMake
```
sudo apt -y install build-essential cmake
```
#### Python 
```
sudo apt -y install python3 python3-doc python3-pip
python3 -m pip install --upgrade pip cmake scikit-build
```
### Install GROMACS  
Open terminal, then copy and paste these lines:
```
wget https://ftp.gromacs.org/gromacs/gromacs-2023.tar.gz
tar xfz gromacs-2023.tar.gz
cd gromacs-2023
mkdir build
cd build
cmake .. -DGMX_BUILD_OWN_FFTW=ON -DREGRESSIONTEST_DOWNLOAD=ON
make -j 4
make -j 4 check
sudo make install
cd
rm gromacs-2023.tar.gz
rm -rf gromacs-2023
```
**NOTE**: If your machine/system supports more (or less) of 4 jobs, you can change `-j` option value.  
Checking your installation and using GROMACS:  
```
source /usr/local/gromacs/bin/GMXRC
gmx
```
#### Install gmxapi  
To use GROMACS with Python
```
python3 -m pip install --upgrade cmake scikit-build gmxapi
```
### Uninstall GROMACS
It is sufficient to delete the following folder
```
cd /usr/local/
sudo rm -rf gromacs
```
then remove eventual GROMACS's environment variable and uninstall `gmxapi` pip package
```
python3 -m pip uninstall gmxapi
```
