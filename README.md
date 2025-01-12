## ros2foxy-rpi-bullseye64
compile ros2 foxy on compute module 4 with Raspberry Pi OS - bullseye 64-bit
Setting up the locale ensures that the system uses UTF-8 encoding, which is necessary for many ROS 2 components to handle text correctly, especially for internationalization and Unicode support.

# install dependencies
```
sudo apt install libfastcdr-dev
sudo apt install liburdfdom-headers-dev
sudo apt install liblog4cxx-dev
sudo python3 -m pip install ifcfg
sudo apt install libasio-dev
sudo apt install libtinyxml2-dev
sudo apt install libcunit1-dev
sudo apt install gnupg2
sudo apt install software-properties-common
sudo apt install libncurses5-dev
sudo apt install libnss3-dev
sudo apt install libreadline-dev
sudo apt install libffi-dev
sudo apt install libsqlite3-dev
sudo apt install libyaml-cpp-dev
sudo apt install libgmock-dev
sudo apt install libx11-dev
sudo apt install libxaw7-dev
sudo apt install qt5-qmake
sudo apt install qtbase5-dev
sudo apt install libogre-1.9-dev
sudo apt install libcurl4-openssl-dev
sudo apt install libfastrtps-dev
sudo apt install '^libxcb.*-dev'
sudo apt install libx11-xcb-dev
sudo apt install libxrender-dev
sudo apt install libxi-dev
sudo apt install libxkbcommon-dev
sudo apt install libxkbcommon-x11-dev
sudo apt install libxslt-dev
sudo apt install libxcursor-dev
sudo apt install libxcomposite-dev
sudo apt install libxdamage-dev
sudo apt install libxrandr-dev
sudo apt install libxtst-dev
sudo apt install libxss-dev
sudo apt install libdbus-1-dev
sudo apt install libevent-dev
sudo apt install libfontconfig1-dev
sudo apt install libcap-dev
sudo apt install libpulse-dev
sudo apt install libudev-dev
sudo apt install libpci-dev
sudo apt install libasound2-dev
sudo apt install libegl1-mesa-dev
sudo apt install freeglut3-dev
sudo apt install libbullet-dev
sudo apt install libopencv-dev
sudo python3 -m pip install colcon-common-extensions
sudo python3 -m pip install setuptools==58.0.4
sudo pip uninstall empy
sudo python3 -m pip install empy==3.3.4
sudo python3 -m pip install lark
sudo apt install cmake
```

# compile sip-4.19.24 and PyQt5-5.15.2
`cd /usr/src
sudo wget https://www.riverbankcomputing.com/static/Downloads/sip/4.19.24/sip-4.19.24.tar.gz
sudo wget https://files.pythonhosted.org/packages/28/6c/640e3f5c734c296a7193079a86842a789edb7988dca39eab44579088a1d1/PyQt5-5.15.2.tar.gz
sudo tar xzf sip-4.19.24.tar.gz
sudo tar xzf PyQt5-5.15.2.tar.gz
cd sip-4.19.24
sudo python3 configure.py --sip-module PyQt5.sip
sudo make -j$(nproc)
sudo make install
cd ../PyQt5-5.15.2
sudo python3 configure.py --qmake /usr/bin/qmake --confirm-license
sudo make -j$(nproc)
sudo make install`

# download source code of the ROS 2 foxy and compile it
`mkdir -p ~/ros2_foxy/src
cd ~/ros2_foxy
wget https://raw.githubusercontent.com/ros2/ros2/foxy/ros2.repos
sudo python3 -m pip install vcstool
vcs import src < ros2.repos
colcon build`

