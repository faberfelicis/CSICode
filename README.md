# Reaper CSI - linux build

## Description
Attempt to build reaper CSI extension on linux. CSI extension (source code available at https://github.com/FunkybotsEvilTwin/CSICode) is only supported on Win & MacOS.  
The approach is to setup CMake with a specific focus on the linux platform while keeping the multi-platform capabilities of CMake (Win32 & Apple).  
The template for the CMake configuration is shared at https://github.com/ak5k/reaper-sdk-vscode.  

So far no changes to the CSI code base is planned, the only elements added in the git linux-build-branch are :  
- CMakeLists.txt configuration file, with some path updates
- /reaper_csurf_integrator/CMakeLists.txt configuration file
- /cmake directory and xxx.cmake configuration files for external packages
- config.h.in  
- remove /WDL : this is replaced by a pull of the source WDL git repository at configuration time and a symlink

## Build

## Install