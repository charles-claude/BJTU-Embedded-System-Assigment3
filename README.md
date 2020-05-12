# BJTU-Embedded-System-Assigment3

Repository for the builded kernel of assignment 3, BJTU Embedded System.
Louison HARIZI 19129047
Charles CLAUDE 19129127

## Assignment 3, Kernel Building for Raspberry Pi 4B


Step 1:  
	We install the official raspberry toolchain from github.
```bash
git clone https://github.com/raspberrypi/tools ~/tools
```
And modify the $PATH environment variable to indicate the files location to the cross compiler.
```bash
echo PATH=\$PATH:~/tools/arm-bcm2708/arm-linux-gnueabihf/bin >> ~/.bashrc
source ~/.bashrc
```

Step 2:  
	We download minimal source required for building:
```bash
git clone --depth=1 https://github.com/raspberrypi/linux
```
And we install all required dependencies:
```bash
sudo apt install git bc bison flex libssl-dev make libc6-dev libncurses5-dev
```
Step3:  
	We go into the correct directory, set the correct configuration and launch the cross compilation.
```bash
cd linux
KERNEL=kernel7l
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- bcm2711_defconfig
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage modules dtbs
```
