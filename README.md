<h1>Intel RealSense Camera D435i</h1>
<h2>A brief description of the Installation process</h2>
<h3>Installation on Windows</h3>

 For Windows it's simple and straight forward.
 You can install the Intel SDK software from [Intel website](www.intelrealsense.com/sdk-2/)

<h3>Installation on Linux</h3>

 Installing the packages:

Add Intel server to the list of repositories :

$ echo 'deb http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo xenial main' | sudo tee /etc/apt/sources.list.d/realsense-public.list

It is recommended to backup /etc/apt/sources.list.d/realsense-public.list file in case of an upgrade.

Register the server’s public key :

$ sudo apt-key adv --keyserver keys.gnupg.net --recv-key 6F3EFCDE

Refresh the list of repositories and packages available :

$ sudo apt-get update

In order to run demos install:

$ sudo apt-get install librealsense2-dkms
$ sudo apt-get install librealsense2-utils

The above two lines will deploy librealsense2 udev rules, kernel drivers, runtime library and executable demos and tools. Reconnect the Intel RealSense depth camera and run: 
$ realsense-viewer

Developers shall install additional packages:

$ sudo apt-get install librealsense2-dev
$ sudo apt-get install librealsense2-dbg

With dev package installed, you can compile an application with librealsense using:
$ g++ -std=c++11 filename.cpp -lrealsense2 or an IDE of your choice.

Verify that the kernel is updated :
modinfo uvcvideo | grep "version:" should include realsense string

<h3>Libraries/Packages</h3>
Prerequisites:
 Some necessaty packages (by the time of writing - 04.2020) work only on Python versions lower than 3.7.
 Therefore a python 3.6 would work fine.

In order to work with the RealSense camera, using Python, we need 2 most important libraries: **librealsense2** and **pyrealsense**
With Python 3.6 you can install them using:

$ pip install librealsense2

$ pip install pyrealsense

Details about **librealsense2** can be found [here](https://github.com/IntelRealSense/librealsense)

Details about **pyrealsense** can be found [here](https://pypi.org/project/pyrealsense/)

<h3>Installation on Raspbian OS</h3>

Installing the RealSense SDK on Raspbian OS is same as for Linux

The libraries **librealsense2** and **pyrealsense** are not available for the OS just by installing them with pip.
One version is to compile the libraries. 

The stept I have followed are in [this link](https://github.com/IntelRealSense/librealsense/blob/master/doc/installation_raspbian.md)

This proccess takes a lot of time (more than 20h - the time I personally needed) because the RaspberryPi is slow and the commands like **cmake**, **make -j1**, **make install** take many hours.
In the end, some of the command gave errors and the whole installation process was *unsuccessful* 

In order to woth with the **RealSense** camera, a different approach should be found. 
 - One alternative is to install Ubuntu on the RaspberryPi
 - Another alternative is to find different ways to install the libraries for Python
 - A third alternative is to try using C/C++ instead of Python.
 
<h4>Other things to mention</h4>

The RealSense Camera works best with USB 3 but so far, were no problems connecting to USB 2
