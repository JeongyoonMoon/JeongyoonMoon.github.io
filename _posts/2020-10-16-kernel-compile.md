---
title: How to compile the Linux kernel
Categories: [Linux Kernel]
Tags: [Linux, Kernel]
---

## How to build the Linux kernel (using kernel package)
0. **Download dependent packages**
	```shell
	# apt install build-essential libncurses5-dev bison flex libssl-dev \
	libelf-dev bin86 kernel-package
	```

2. **Download the kernel source file.**
	Download the .tar.xz file from http://kernel.org .
	
	```shell
	# xz -d [*.tar.xz]
	# tar xvf [*.tar]
	```
	* Usually install in `/usr/src/` directory (root privilege required).

3. **make config**
	``` shell
	# cd [path-to-linux-src]
	# cp /boot/config-$(uname -r) ./.config
	# make menuconfig
	```
	Change the current directory to the Linux source file folder and copy configuration file of the current Linux kernel.
	* `make menuconfig`:  Config using GUI.  (alternatives: `make config`, `make xconfig`, ...)

4. **make**
	```shell
	# make-kpkg clean
	# make-kpkg -j# --initrd kernel_image
	# dpkg -i ../[linux_image_file]
	```
	* `-j#` option: # of threads for compile, typically equals to # of CPU.
	* .deb file will be created in `..` after `make-kpkg`

5. **reboot**
	```shell
	# reboot
	```
	*	Check whether the kernel version changes with  `$ uname -r `.

---
### Reference

https://harryp.tistory.com/9 (in Korean)

https://manpages.ubuntu.com/manpages/precise/man1/make-kpkg.1.html

http://man.he.net/man5/kernel-package
