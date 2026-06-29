This page will guide you through all the required steps to compile the server core on Windows. We also have a [video tutorial](https://www.youtube.com/watch?v=dDQs1t5fZWo) on the subject for people who are not into reading.

### Required software:
- [Microsoft Visual Studio](https://www.visualstudio.com/vs/visual-studio-express/) ([click here for 2015](https://go.microsoft.com/fwlink/?LinkId=615448&clcid=0x409))
- [CMake](https://cmake.org/download/)
- [Git](https://git-scm.com/download/win)

Before you jump into it, you need to have the above programs already installed.

## 1. Downloading the source code

To download the server code, first open the command prompt, then navigate to the folder you wish to download it in using the "cd" command to change directories. Once you are there type the following to clone the repository.
```
git clone -b development http://github.com/vmangos/core
```
This will make a local copy of the code which you can use to compile the server, but you cannot contribute back any fixes this way. If you wish to be able to make pull requests with your changes, then you need to fork the repository and make a new branch on your fork.

## 2. Configuring the project with CMake

Once you have downloaded the source code, make a new folder named "build" next to the "core" folder. Now open CMake and paste the path to those folders at the top. Click on Configure and choose which version of Visual Studio you will be using. If you want to compile for x64 then select the Win64 version. You will see a bunch of settings show up. The only ones you need to worry about are "CMAKE_INSTALL_PREFIX" and "PREFIX". This is the directory in which the binary files will be copied once you build the project. After you've changed them to whatever you want, click on Configure again and finally on Generate.

![](https://i.imgur.com/PNP5bYT.gif)

You should now find the solution file inside the "build" folder.

## 3. Building the server core

Go to "build" and open the "MaNGOS.sln" project in Visual Studio. The first thing you need to do after loading the solution file is to change the configuration to Release. Then simply right click on ALL_BUILD, press Build and wait.

Go to the next tutorial to learn how to setup your database and extract data files.

![](https://i.imgur.com/FJg0maH.gif)

When it finishes building, right click on INSTALL and press build again. You will now find the compiled server binaries inside the install directory you specified when configuring with CMake.

Go to the [next tutorial](Getting-it-working-Windows.md) to learn how to setup your database and extract data files.
