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
Step 3:  
We go into the correct directory, set the correct configuration and launch the cross compilation.
```bash
cd linux
KERNEL=kernel7l
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- bcm2711_defconfig
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage modules dtbs
```

Now we need to install Qemu to run our custom kernel.  
It can be downloaded from the official website : https://www.qemu.org/
We also have to dowload a official resbian image from https://www.raspberrypi.org/downloads/raspbian/

Then we are ready to run our Raspberry pi on Qemu using the following command inside a Windows Powershell:

```powershell
qemu-system-arm -M versatilepb -cpu arm1176 -m 256 -hda .\2020-02-13-raspbian-buster.img -kernel .\kernel -append 'root=/dev/sda2 panic=1' -no-reboot
```

We can see the result on the following screenshots :

The start of Raspbian booting in Qemu:
![Raspbian booting](https://github.com/charles-claude/BJTU-Embedded-System-Assigment3/blob/master/screenshots/embedded_screen1.png)

Raspbian working perfectly
![Raspbian booting](https://github.com/charles-claude/BJTU-Embedded-System-Assigment3/blob/master/screenshots/embedded_screen2.png)
