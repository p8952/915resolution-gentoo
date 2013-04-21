915Resolution: Intel Video BIOS Hack
====================================

From : http://915resolution.mango-lang.org/
-------------------------------------------
915resolution is a tool to modify the video BIOS of the 800 and 900 series 
Intel graphics chipsets. This includes the 830, 845G, 855G, and 865G chipsets, 
as well as 915G, 915GM, 945G, 946GZ, G965, and Q965 chipsets. This modification 
is necessary to allow the display of certain graphics resolutions for an Xorg 
or XFree86 graphics server.

In Gentoo
---------
915resolution has been removed from Gentoo's portage tree, it is also no longer
needed with Xorg when using newer versions of Intel video drivers although when
running off the framebuffer it is still needed.

Simple Usage
------------
1) Ensure your make.conf is setup to use local ebuilds:
    PORTDIR_OVERLAY="/usr/local/portage/"

2) Download the ebuild and install:
    cd /usr/local/portage/
    wget https://github.com/p8952/915resolution-gentoo/archive/master.tar.gz
    tar xvf master.tar.gz
    mv 915resolution-gentoo-master/sys-apps .
    emerge -av 915resolution
    
3) Change your framebuffer resolution:
    emerge -av klibc v86d
    915resolution 5c 800 480 32
    modprobe uvesafb mode_option=800x480-32@60

The later two need to be run every boot, you can either use the 915resolution
and uvesafb init scripts or just dump the commands into /etc/local.d/fb.start

More Info:
----------
Further reading on 915resolution and uvesafb.

http://915resolution.mango-lang.org/
http://en.gentoo-wiki.com/wiki/Asus_Eee_PC_701#Framebuffer
http://wiki.gentoo.org/wiki/Uvesafb
https://wiki.archlinux.org/index.php/Uvesafb
