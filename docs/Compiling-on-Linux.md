# Compiling on Linux

This page will guide you through all the required steps to compile the server core on Linux.

### Required software:

- g++ Compiler
- CMake
- Git

### Required dependencies:

- MariaDB or MySQL 5.5 (officially supported by VMaNGOS, though EOL). MySQL 8.0 is not supported.
- OpenSSL (if not on Arch)
- Zlib

## 1. Installing essential compiler packages

### Debian, Ubuntu

```
sudo apt install build-essential
```

### Arch

```
sudo pacman -S base-devel
```

### Fedora

```
sudo dnf install make gcc g++
```

## 2. Installing Git

To download the source code for VMaNGOS, you should install Git. This can be avoided if you choose to manually download the zip archive from the website, but it's better to use Git, as it makes pulling updates from the main repository much easier.

### Debian, Ubuntu

```
sudo apt install git
```

### Arch

```
sudo pacman -S git
```

### Fedora

```
sudo dnf install git
```

## 3. Installing CMake

Since this is a cross-platform project, we use CMake to generate the appropriate solution files for every environment.

### Debian, Ubuntu

```
sudo apt install cmake
```

### Arch

```
sudo pacman -S cmake
```

### Fedora

```
sudo dnf install cmake
```

## 4. Installing MariaDB or MySQL

Account, character, and game data is stored inside the database, so we need MariaDB to read and write data to it.

> **MySQL 5.5** is officially supported by VMaNGOS but is end-of-life and unavailable in modern distribution repositories. If you choose MySQL 5.5, refer to your distribution's documentation or community guides for manual installation steps. **MySQL 8.0 is not supported.**

Below is how to install **MariaDB** on common distributions:

### Debian, Ubuntu

```
sudo apt-get install mariadb-server libmariadb-dev
systemctl enable --now mariadb.service
```

### Arch

```
sudo pacman -S mariadb mariadb-libs
systemctl enable --now mariadb.service
```

### Fedora

```
sudo dnf install mariadb-server mariadb-devel
systemctl enable --now mariadb.service
```

## 5. Installing OpenSSL

Communication between the game client and server needs to be encrypted, which requires a cryptography library.

### Debian, Ubuntu

```
sudo apt-get install openssl
sudo apt-get install libssl-dev
```

### Arch

OpenSSL is preinstalled on Arch and provided by the `openssl` package; no extra steps are needed.

### Fedora

```
sudo dnf install openssl
sudo dnf install openssl-devel
```

## 6. Installing Zlib

In order to reduce network traffic, a number of packets sent from the server are compressed, so we need a library for that too.

### Debian, Ubuntu

```
sudo apt install zlib1g-dev -y
```

### Arch

On arch we can use zlib-ng-compat, which is faster.
```
sudo pacman -S zlib-ng-compat
```

### Fedora

On Fedora we have to use zlib-ng-compat as zlib package has been deleted in Fedora 40+.
```
sudo dnf install zlib-ng-compat zlib-ng-compat-devel
```

## 7. Downloading the source code

Clone the latest core revision into a vmangos directory inside your home folder using Git:
```
mkdir ~/vmangos
cd ~/vmangos
git clone -b development https://github.com/vmangos/core
```

## 8. Configuring with CMake

Now let's configure our project. Make another directory called `build` next to the newly created `core` folder, and call CMake from there to generate the Makefiles.
```
mkdir build
cd build
cmake ../core -DCMAKE_BUILD_TYPE=Release -DSUPPORTED_CLIENT_BUILD=5875 -DUSE_EXTRACTORS=0 -DCMAKE_INSTALL_PREFIX=~/vmangos
```

As you can see, you'll need to set a couple of settings when calling CMake. Here is what each of these means.

#### -DCMAKE_BUILD_TYPE=Release

This setting lets you choose if you want to compile in Debug or Release mode. The server will run much smoother in Release mode, so set -DCMAKE_BUILD_TYPE to Release.

#### SUPPORTED_CLIENT_BUILD=5875

Since this is a progressive emulator, you can specify the exact client version to support. The build number of the final Vanilla patch 1.12.1 is 5875. You can see your client's build number in the lower left corner of the login screen. Only the final version of each major patch is supported. That means you can play with 1.8.4, but not 1.8.0 for example.

#### USE_EXTRACTORS=0

The server needs the map terrain data in order to know where anything is located. This data is extracted from the game client using several tools, which you can choose to build with this setting. If you already have the map files from somewhere else, then you can set this to 0.

#### CMAKE_INSTALL_PREFIX=~/vmangos

This setting lets you choose where to copy the binaries after compilation finishes.

## 9. Compiling the core

Now that we have all the dependencies, and the project files have been properly configured, we can go ahead and compile the core. This can take quite a while, depending on the computer you are using.
```
make -j$(nproc)
make install
```

Congratulations! You should now be able to find the compiled binaries inside the `vmangos` directory.

Go to the [next tutorial](Getting-it-working-Linux.md) to learn how to setup your database and extract data files.
