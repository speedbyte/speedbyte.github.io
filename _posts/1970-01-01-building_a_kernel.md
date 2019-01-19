---
layout: post
---

reduced-algebra
sage
maxima

lists all printers in network
avahi-browse -a | grep Printer

sysv-rc-conf
BrowseProtocols None in /etc/cups

arping -c 1 -I enp0s25 134.2.15.254


Raspberry

ARCH=arm CCPREFIX=${}

Ubuntu:

Simply get
No source code compiling necessary. The config file cannot be given here i.e the kernel cannot be configured.
They re prebuilt binary packages.
http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.9/
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8/linux-headers-4.8.0-040800-generic_4.8.0-040800.201610022031_amd64.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8/linux-headers-4.8.0-040800_4.8.0-040800.201610022031_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8/linux-image-4.8.0-040800-generic_4.8.0-040800.201610022031_amd64.deb
and run sudo dpkg -i

http://kernel.ubuntu.com/git/kernel-ppa/mirror/ubuntu-xenial.git/

Applying Patches:

cd /usr/src
wget http://www.kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.19-rc4.bz2
cd /usr/src/linux
bzip2 -dc /usr/src/patch-2.6.19-rc4.bz2 | patch -p1 --dry-run
bzip2 -dc /usr/src/patch-2.6.19-rc4.bz2 | patch -p1

The below two have become a  part of make install, hence update-initramfs neednot be done explicitly.
update-initramfs or mkinitfs tool
update-grub

update-initramfs -c -k 3.3.3

CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

Skip Debug should be set to true before building
sudo apt-get install pkg-config-dbgsym
fakeroot debian/rules clean
fakeroot debian/rules binary-headers binary-generic binary-perarch skipdbg=false



Since the 2.6.32 kernel, a new feature allows you to
update the configuration to only compile modules that are actually used
in your system:
make localmodconfig


pt-get install linux-image-4.8.0-29-generic
Kernel 4.8


agrawal-local@jcbose:/local/development/ubuntu-xenial$ sudo make install
sh ./arch/x86/boot/install.sh 4.4.44+ arch/x86/boot/bzImage \
System.map "/boot"
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.44+ /boot/vmlinuz-4.4.44+
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.44+ /boot/vmlinuz-4.4.44+
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.44+ /boot/vmlinuz-4.4.44+

update-initramfs: Generating /boot/initrd.img-4.4.44+
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.44+ /boot/vmlinuz-4.4.44+
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.44+ /boot/vmlinuz-4.4.44+
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 4.4.44+ /boot/vmlinuz-4.4.44+

P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-4.4.44+...
P: Writing config for /boot/vmlinuz-4.4.0-34-generic...
P: Writing config for /boot/vmlinuz-3.19.0-66-generic...
P: Writing config for /boot/vmlinuz-3.19.0-43-generic...
P: Writing config for /boot/vmlinuz-3.19.0-42-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.

run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.44+ /boot/vmlinuz-4.4.44+
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.44+
Found initrd image: /boot/initrd.img-4.4.44+
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found linux image: /boot/vmlinuz-3.19.0-66-generic
Found initrd image: /boot/initrd.img-3.19.0-66-generic
Found linux image: /boot/vmlinuz-3.19.0-43-generic
Found initrd image: /boot/initrd.img-3.19.0-43-generic
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.3 LTS (14.04) on /dev/sda1




Filesystem      Size  Used Avail Use% Mounted on
udev            4,1G   13k  4,1G   1% /dev
tmpfs           805M  1,8M  803M   1% /run
/dev/sda9        42G   38G  2,0G  95% /
none            4,1k     0  4,1k   0% /sys/fs/cgroup
none            5,3M     0  5,3M   0% /run/lock
none            4,1G  304k  4,1G   1% /run/shm
none            105M   54k  105M   1% /run/user
/dev/sda10       47G   22G   24G  49% /matlab
/dev/sda8        99G   71G   24G  76% /local



EXTRAVERSION
CONFIG_MODVERSION

kallsym
modules
/lib/modules/version/modules.dep
meminfo
devices

Major and Minor number.
Accessing kernel space through /dev/

mknod /dev/coffee c 12 2

proc means processes and not processor

sys_call_table is the place where all the pointers to the system calls are present.

If one wants to write to a file system, the user process has to go through the write system call. The write system call since is a kernel mode,
the hardware needs to unlock the hardware area by letting the kernel mode get the system mode in ARM for example. This happens over a change in mode through interrupts.

Example a socket read.  If the read is a blocking call, the process goes to sleep and activates the wait_irq. As soon as something happens on teh file which the socket was supposed to read, the process is woken up and it does the respective thing.
