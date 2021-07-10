# SpaceOcean (spacecoin-qt) #

![Spacecoin Logo](https://i.imgur.com/FlGoFAz.png "Spacecoin Logo")

![Downloads](https://img.shields.io/github/downloads/SpaceWorksCo/SpaceOcean/total)
[![Version](https://img.shields.io/github/v/release/SpaceWorksCo/SpaceOcean?include_prereleases)](https://github.com/SpaceWorksCo/SpaceOcean/releases)

Spacecoin-Qt (SpaceOcean) is a Qt native full node wallet for [Spacecoin  (SPACE)](https://spacecoin.network).

It's available for three OS platforms - Windows, Linux, MacOS.

Download from [Releases](https://github.com/SpaceWorksCo/SpaceOcean/releases) or follow the steps below to build from source.

Visit the `#spacecoin-qt` channel on the [Spacecoin Discord](https://spacecoin.network/discord) for support and more discussion.


## How to build?

- Linux: `build.sh` (native build)
- Windows: `build-win.sh` (cross-compilation for Win)
- MacOS: `build-mac-cross.sh` (cross-compilation for OSX)
- MacOS: `build-mac.sh` (native build)

#### Linux

```shell
#The following packages are needed:
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl
```

```shell
git clone https://github.com/SpaceWorksCo/SpaceOcean --branch static-spacecoin --single-branch
cd SpaceOcean
./zcutil/fetch-params.sh
# -j8 = using 8 threads for the compilation - replace 8 with number of threads you want to use
./zcutil/build.sh -j8
#This can take some time.
```

#### OSX (Cross-compile)

Before start, read the following docs: [depends](https://github.com/bitcoin/bitcoin/blob/master/depends/README.md), [macdeploy](https://github.com/bitcoin/bitcoin/blob/master/contrib/macdeploy/README.md) .

Install dependencies:
```
sudo apt-get install curl librsvg2-bin libtiff-tools bsdmainutils cmake imagemagick libcap-dev libz-dev libbz2-dev python3-setuptools libtinfo5 xorriso
```

Place prepared SDK file `Xcode-11.3.1-11C505-extracted-SDK-with-libcxx-headers.tar.gz` in repo root, use `build-mac-cross.sh` script to build.

#### OSX (Native)
Ensure you have [brew](https://brew.sh) and Command Line Tools installed.
```shell
# Install brew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
# Install Xcode, opens a pop-up window to install CLT without installing the entire Xcode package
xcode-select --install
# Update brew and install dependencies
brew update
brew upgrade
brew tap discoteq/discoteq; brew install flock
brew install autoconf autogen automake
# brew install gcc@6
brew install binutils
brew install protobuf
brew install coreutils
brew install wget

git clone https://github.com/SpaceWorksCo/SpaceOcean --branch static-spacecoin --single-branch
cd SpaceOcean
./zcutil/fetch-params.sh
# -j8 = using 8 threads for the compilation - replace 8 with number of threads you want to use
./zcutil/build-mac.sh -j8
# This can take some time.
```

*p.s.* Currently only `x86_64` arch supported for MacOS, build for `Apple M1` processors unfortunately not yet supported.

#### Windows
Use a debian cross-compilation setup with mingw for windows and run:
```shell
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl cmake mingw-w64
curl https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
rustup target add x86_64-pc-windows-gnu

sudo update-alternatives --config x86_64-w64-mingw32-gcc
# (configure to use POSIX variant)
sudo update-alternatives --config x86_64-w64-mingw32-g++
# (configure to use POSIX variant)

git clone https://github.com/SpaceWorksCo/SpaceOcean --branch static-spacecoin --single-branch
cd SpaceOcean
./zcutil/fetch-params.sh
# -j8 = using 8 threads for the compilation - replace 8 with number of threads you want to use
./zcutil/build-win.sh -j8
#This can take some time.
```

**SpaceOcean is experimental and a work-in-progress.** Use at your own risk.


## Developers of Qt wallet ##
- Spacecoin Fork: **SpaceWorks**
- Main developer: **Ocean**
- IT Expert / Sysengineer: **Decker**
