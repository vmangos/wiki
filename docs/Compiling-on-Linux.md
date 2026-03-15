This page will guide you through all the required steps to compile the server core on Ubuntu or Arch. Compiling VMaNGOS on Linux is much easier than doing it on Windows, since you can install all dependencies through the terminal.

### Required software:
- g++ Compiler
- CMake
- Git

### Required dependencies:
- ACE
- TBB
- MySQL Connector/C or MariaDB
- OpenSSL
- Zlib

## 1. Installing g++

First we need to install the compiler.

### Ubuntu
```
sudo apt install g++
```
### Arch
```
sudo pacman -S gcc
```

## 2. Installing ACE

The ACE library is essential, since it's used for Networking, Threading and File System access.

### Ubuntu
```
sudo apt install -qq libace-dev
export ACE_ROOT=/usr/include/ace
```
### Arch
On Arch we have to use AUR
```
mkdir libace && cd libace
curl -L -O https://aur.archlinux.org/cgit/aur.git/snapshot/ace.tar.gz
makepkg -si
cd .. && rm -rf libace
```

## 3. Installing TBB

The TBB library is used to provide better performance and scalability for memory allocation/deallocation operations in multithreaded applications, compared to the default allocator. This dependency is optional and can be skipped if you specify the USE_STD_MALLOC option when configuring with CMake.

### Ubuntu
```
sudo apt install -y libtbb-dev
export TBB_ROOT_DIR=/usr/include/tbb
```
### Arch
```
sudo pacman -S tbb
export TBB_ROOT_DIR=/usr/include/tbb
```

## 4. Installing Git

To download the source code for VMaNGOS, you should install Git. This can be avoided if you choose to manually download the zip archive from the website, but it's better to use Git, as it makes pulling updates from the main repository much easier.
### Ubuntu
```
sudo apt install git
```
### Arch
```
sudo pacman -S git
```

## 5. Installing CMake

Since this is a cross-platform project, we use CMake to generate the appropriate solution files for every environment.
### Ubuntu
```
sudo apt install cmake
```
### Arch
```
sudo pacman -S cmake
```

## 6 Installing MySQL Connector/C 

Account, character and game data is stored inside the database, so we need the MySQL connector library to read and write data to it.
### Ubuntu
```
sudo apt-get install libmysqlclient-dev
```
### Arch
On Arch good option is to use MariaDB instead of libmysqlclient since it is available in official repositories.
```
sudo pacman -S mariadb
```

## 7. Installing OpenSSL

Communication between the game client and server needs to be encrypted, which requires a cryptography library.
### Ubuntu
```
sudo apt-get install openssl
sudo apt-get install libssl-dev
```
### Arch
OpenSSL is provided as part of coreutils and there is no need to install it.

## 8. Installing Zlib

In order to reduce network traffic, a number of packets sent from the server are compressed, so we need a library for that too.
### Ubuntu
```
sudo apt install build-essential checkinstall zlib1g-dev -y
```
### Arch
```
sudo pacman -S zlib
```

## 9. Downloading the source code

Make a new folder called vmangos, and use Git to download the latest core revision:
```
mkdir vmangos
cd vmangos
git clone -b development https://github.com/vmangos/core
```

## 10. Configuring with CMake

Now let's configure our project. Make another directory called `build` next to the newly created `core` folder, and call CMake from there to generate the Makefiles.
```
mkdir build
cd build
cmake ~/vmangos/core -DDEBUG=0 -DSUPPORTED_CLIENT_BUILD=5875 -DUSE_EXTRACTORS=0 -DCMAKE_INSTALL_PREFIX=~/vmangos
```

As you can see, you'll need to set a couple of settings when calling CMake. Here is what each of these means.

#### DEBUG=0

This setting lets you choose if you want to compile in Debug or Release mode. The server will run much smoother in Release mode, so set Debug to 0.

#### SUPPORTED_CLIENT_BUILD=5875

Since this is a progressive emulator, you can specify the exact client version to support. The build number of the final Vanilla patch 1.12.1 is 5875. You can see your client's build number in the lower left corner of the login screen. Only the final version of each major patch is supported. That means you can play with 1.8.4, but not 1.8.0 for example.

#### USE_EXTRACTORS=1

The server needs the map terrain data in order to know where anything is located. This data is extracted from the game client using several tools, which you can choose to build with this setting. If you already have the map files from somewhere else, then you can set this to 0.

#### CMAKE_INSTALL_PREFIX=~/vmangos

This setting lets you choose where to copy the binaries after compilation finishes.

## 11. Compiling the core

Now that we have all the dependencies, and the project files have been properly configured, we can go ahead and compile the core. This can take quite a while, depending on the computer you are using.
```
make -j4
make install
```

Congratulations! You should now be able to find the compiled binaries inside the `vmangos` directory.

Go to the [next tutorial](Getting-it-working.md) to learn how to setup your database.
