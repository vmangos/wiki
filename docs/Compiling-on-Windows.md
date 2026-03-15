This page will guide you through all the required steps to compile the server core on Windows. We also have a [video tutorial](https://www.youtube.com/watch?v=dDQs1t5fZWo) on the subject for people who are not into reading.

### Required software:
- [Microsoft Visual Studio](https://www.visualstudio.com/vs/visual-studio-express/) ([click here for 2015](https://go.microsoft.com/fwlink/?LinkId=615448&clcid=0x409))
- [CMake](https://cmake.org/download/)
- [Git](https://git-scm.com/download/win)

Before you jump into it, you need to have the above programs already installed.

### Required dependencies:
- [ACE](http://download.dre.vanderbilt.edu/) ([click here for exact version used in the guide](https://github.com/DOCGroup/ACE_TAO/releases/tag/ACE%2BTAO-6_4_2))
- [TBB](https://github.com/oneapi-src/oneTBB/releases/tag/2017_U3) ([click here for exact version used in the guide](https://github.com/oneapi-src/oneTBB/releases/tag/2017_U3))

There are also several required libraries on which the project depends. Go ahead and download the latest versions of those as well.

## 1. Installing ACE

Download the latest ACE micro release, then extract it to C:\ACE_wrappers
![](https://i.imgur.com/IDzJq2a.gif)

Now go into C:\ACE_wrappers\ace\, create a file named Config.h and paste this into it:
> #include "ace/config-win32.h"

![](https://i.imgur.com/Qcvimld.gif)

You can now open ACE_wrappers_vc14.sln and build the project with Visual Studio. Remember to switch the configuration to Release before pressing Build! If you wish to build for x64 then change the neighboring setting from Win32 to Win64.
![](https://i.imgur.com/FuGIrqB.gif)

## 2. Installing TBB

Download the latest TBB stable release and extract it to C:\tbb
![](https://i.imgur.com/YlKRJuS.gif)

## 3. Setting up the environment variables

In order to use the dependencies we just installed, you must add the path to your environmental variables.

Right click on My Computer -> Properties -> Advanced system settings -> Advanced -> Environment Variables -> New

![](https://i.imgur.com/oQrCpfR.gif)

Now type ACE_ROOT for name and C:\ACE_wrappers\ for value. Do it again but this time type TBB_ROOT and C:\tbb\ instead.

## 4. Downloading the source code

To download the server code, first open the command prompt, then navigate to the folder you wish to download it in using the "cd" command to change directories. Once you are there type the following to clone the repository.

> git clone -b development http://github.com/vmangos/core

This will make a local copy of the code which you can use to compile the server, but you cannot contribute back any fixes this way. If you wish to be able to make pull requests with your changes, then you need to fork the repository and make a new branch on your fork.

## 5. Configuring the project with CMake

Once you have downloaded the source code, make a new folder named "build" next to the "core" folder. Now open CMake and paste the path to those folders at the top. Click on Configure and choose which version of Visual Studio you will be using. If you want to compile for x64 then select the Win64 version. You will see a bunch of settings show up. The only ones you need to worry about are "CMAKE_INSTALL_PREFIX" and "PREFIX". This is the directory in which the binary files will be copied once you build the project. After you've changed them to whatever you want, click on Configure again and finally on Generate.

![](https://i.imgur.com/PNP5bYT.gif)

You should now find the solution file inside the "build" folder.

## 6. Building the server core

Go to "build" and open the "MaNGOS.sln" project in Visual Studio. The first thing you need to do after loading the solution file is to change the configuration to Release. Then simply right click on ALL_BUILD, press Build and wait.

![](https://i.imgur.com/FJg0maH.gif)

When it finishes building, right click on INSTALL and press build again. You will now find the compiled server binaries inside the install directory you specified when configuring with CMake.