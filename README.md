# Reaper CSI - linux build

## Description
Attempt to build reaper CSI extension on linux. CSI extension (source code available at https://github.com/FunkybotsEvilTwin/CSICode) is only supported on Win & MacOS.  
The approach is to setup CMake with a specific focus on the linux platform while keeping the multi-platform capabilities of CMake (Win32 & Apple).  
The template for the CMake configuration is shared at https://github.com/ak5k/reaper-sdk-vscode. Please visit this page as this is a great ressource to understand how to setup a multiplatform development environment for Reaper extensions using Visual Studio Code and CMake.

So far there is no change to the CSI code base. The only elements added in the git linux-build-branch are :  
- CMakeLists.txt configuration file, with some path updates
- /reaper_csurf_integrator/CMakeLists.txt configuration file
- /cmake directory and xxx.cmake configuration files for external packages
- config.h.in  
- remove /WDL : this is replaced by a pull of the source WDL git repository at configuration time and a symlink

## Build
Please refer to https://github.com/ak5k/reaper-sdk-vscode for setting up your environment.
At least you should install the following :
```
sudo apt install build-essential cmake gdb git valgrind perl
```  
Then you have get locally a copy of the git linux-build-branch :  

```
git clone https://github.com/faberfelicis/CSICode
cd CSICode
git branch -r
git checkout linux-build-branch
```  

Configure CMake :  
```
mkdir build
cd build
cmake ..
```  

Generate ressources :
```
cd ../reaper_csurf_integrator
perl ../WDL/swell/swell_resgen.pl res.rc
```
Todo : include this generation step in the CMake configuration process


Build :
```
cd ../build
make  # or `cmake --build .` on Windows
```


## Install

Copy the reaper_csurf_integrator-x86_64.so from the build directory to ~/.config/REAPER/UserPlugins (this depends on you Reaper setup).  
Refer to https://github.com/FunkybotsEvilTwin/CSI_Install for completing your installation.  
A very comprehensive wiki is available at https://github.com/FunkybotsEvilTwin/CSIUserGuide/wiki for detailed instructions.  
Please note that I have some hard crash if the CSI support files are not properly setup. Fixing this would required some CSI code updates to check for the existence of files / directories. In particular, the Surface.txt file has to be named with a capital S otherwise it is not found.