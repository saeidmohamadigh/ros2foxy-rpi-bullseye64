## ros2foxy-rpi-bullseye64
compile ros2 foxy on compute module 4 with Raspberry Pi OS - bullseye 64-bit
Setting up the locale ensures that the system uses UTF-8 encoding, which is necessary for many ROS 2 components to handle text correctly, especially for internationalization and Unicode support.

# install dependencies
'''
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
'''

