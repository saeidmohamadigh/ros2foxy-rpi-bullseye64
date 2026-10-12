# ROS 2 Foxy on Raspberry Pi OS Bullseye 64-bit (Compute Module 4)

A complete guide to compile and install **ROS 2 Foxy** from source on **Raspberry Pi OS Bullseye (64-bit)** running on the **Compute Module 4**.

> **Note**: ROS 2 Foxy reached End-of-Life in June 2023. This repository is intended for users who still need Foxy on modern Raspberry Pi OS (Bullseye) hardware.

## Features

- Full source build of ROS 2 Foxy
- Tested on Compute Module 4 + Raspberry Pi OS Bullseye 64-bit
- Includes required SIP and PyQt5 builds
- Step-by-step, reproducible instructions

## Requirements

| Item                    | Recommendation                  |
|-------------------------|---------------------------------|
| Hardware                | Compute Module 4 (or Pi 4/400)  |
| OS                      | Raspberry Pi OS Bullseye 64-bit |
| RAM                     | 4 GB minimum (8 GB recommended) |
| Free Disk Space         | ~12–15 GB                       |
| Internet                | Stable connection required      |
| Build time              | Several hours (depending on hardware) |

It is highly recommended to enable a swap file if you have less than 8 GB of RAM.

## Installation

### 1. Set Locale (Required)

ROS 2 requires UTF-8 locale:

```bash
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
```

### 2. Install System Dependencies

```bash
sudo apt update
sudo apt install -y \
  libfastcdr-dev \
  liburdfdom-headers-dev \
  liblog4cxx-dev \
  libasio-dev \
  libtinyxml2-dev \
  libcunit1-dev \
  gnupg2 \
  software-properties-common \
  libncurses5-dev \
  libnss3-dev \
  libreadline-dev \
  libffi-dev \
  libsqlite3-dev \
  libyaml-cpp-dev \
  libgmock-dev \
  libx11-dev \
  libxaw7-dev \
  qt5-qmake \
  qtbase5-dev \
  libogre-1.9-dev \
  libcurl4-openssl-dev \
  libfastrtps-dev \
  '^libxcb.*-dev' \
  libx11-xcb-dev \
  libxrender-dev \
  libxi-dev \
  libxkbcommon-dev \
  libxkbcommon-x11-dev \
  libxslt-dev \
  libxcursor-dev \
  libxcomposite-dev \
  libxdamage-dev \
  libxrandr-dev \
  libxtst-dev \
  libxss-dev \
  libdbus-1-dev \
  libevent-dev \
  libfontconfig1-dev \
  libcap-dev \
  libpulse-dev \
  libudev-dev \
  libpci-dev \
  libasound2-dev \
  libegl1-mesa-dev \
  freeglut3-dev \
  libbullet-dev \
  libopencv-dev \
  cmake \
  python3-pyqt5.qtsvg \
  graphviz
```

### 3. Install Python Dependencies

```bash
sudo python3 -m pip install --upgrade pip
sudo python3 -m pip install ifcfg colcon-common-extensions setuptools==58.0.4 lark pydot
sudo pip uninstall -y empy
sudo python3 -m pip install empy==3.3.4
sudo python3 -m pip install vcstool
```

### 4. Build SIP and PyQt5

```bash
cd /usr/src

# Download source archives from this repository
sudo wget https://github.com/saeidmohamadigh/ros2foxy-rpi-bullseye64/raw/main/sip-4.19.24.tar.gz
sudo wget https://github.com/saeidmohamadigh/ros2foxy-rpi-bullseye64/raw/main/PyQt5-5.15.2.tar.gz

sudo tar xzf sip-4.19.24.tar.gz
sudo tar xzf PyQt5-5.15.2.tar.gz

# Build and install SIP
cd sip-4.19.24
sudo python3 configure.py --sip-module PyQt5.sip
sudo make -j$(nproc)
sudo make install

# Build and install PyQt5
cd ../PyQt5-5.15.2
sudo python3 configure.py --qmake /usr/bin/qmake --confirm-license
sudo make -j$(nproc)
sudo make install
```

### 5. Download and Build ROS 2 Foxy

```bash
mkdir -p ~/ros2_foxy/src
cd ~/ros2_foxy

wget https://raw.githubusercontent.com/ros2/ros2/foxy/ros2.repos
vcs import src < ros2.repos

# Build (this will take a long time)
colcon build --symlink-install
```

### 6. Source the Workspace

Add the following line to your `~/.bashrc` (or run it manually):

```bash
source ~/ros2_foxy/install/setup.bash
```

Then reload:

```bash
source ~/.bashrc
```

## Verification

```bash
ros2 --help
ros2 doctor
```

## Notes & Tips

- The full build can take **4–8+ hours** depending on your hardware and cooling.
- Make sure you have enough free disk space before starting the `colcon build`.
- If the build fails due to memory, increase your swap size.
- Some packages related to visualization (RViz, etc.) may have limitations on headless setups.

## License

This repository is released under the [MIT License](LICENSE).

## Acknowledgments

- [ROS 2](https://github.com/ros2/ros2) community
- Raspberry Pi Foundation
```
