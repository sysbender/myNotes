# MyNote-X11


# reference

vm
    https://mike632t.wordpress.com/2017/07/15/configuring-x-windows-on-a-virtual-machine/
    
headless/dummy




# NICE DCV

1. install nvidia
2. add BusID in xorg.conf



## try dummy 

https://unix.stackexchange.com/questions/651714/multiple-dummy-monitors-on-remote-headless-linux-for-vnc-to-local-multiple-monit


```

root@cos7gpu ~]#  cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```



# An X Window System tutorial (Part 1)

1. window manager 


mouse - sloppy focus
```
xclock -geometry -0-0 &   # right bottom
xterm -geometry +0+0   # left top

```

the last file acts as the control program for the x-windows-system in the x.rc file

ctrl-alt-backspace



# Linux Desktop

desktop environment - KDE, GNOME, XFCE
Xserver - 
    * caves : black screen
    * start : X
    * kill x - ctrl + alt + backspace
 
Windows environment (no windows manager):
    * start : xinit
    
windows manager + file manager
    * twn
    * metacity
Display manager -JDE
    * startx and give a login screen
    

## xorg.conf
1. create config: Xorg -configure
2. use the config : X -config xorg.conf.new
    * monitor
    * mouse
    * keyboard


## choose default 

check /etc/X11/xinit/Xclients

1. one way is add /etc/sysconfig/desktop
```
DESKTOP="KDE"
DISPLAYMANAGER="KDE"

```
2. 2nd way is edit Xclients
   PREFERRED=/usr/bin/startkde
   
   
## start multiple X

startx -- :1

switch to tty 1: ctrl+Alt+F1 

# redhat X system

x client -> Xserver -> Hardware (Video, keyboard, mouse )

X Client : 
* Windows Manage -control postion, resize, move window
    * metacity - for GNOME
    * kwin - for KDE
    * compiz - based on openGL
    * mwm - Motif , standalone, should not be used with GNOME/KDE
    * twm - can be used either as a standalone or with a desktop environment
* Desktop Environment
    * Gnome - based on GTK+ 2
    * KDE - based on QT 4

## X server configuration

executeable 
    * one file /usr/bin/Xorg - symbolic link X
    * other files in /etc/X11 , /usr/share/X11
config
    * /usr/share/X11/xorg.conf.d - vendor or 3rd party
    * xorg.conf.d  - user
    * xorg.conf  - 
loadable module
    * /usr/lib/xorg/modules


configuration structure
```
section "section_name"
    option_name option_value
endSection
```
###  sections
* InputClass - apply to a class of device (not a single device)
* inputDevice - xorg-x11-drv-* provide the auto config through HAL
* ServerFlags - global X server setting, can be overridden in the ServerLayout
* ServerLayout - binds the input and output devices,keyboard and monitor
    *  only first ServerLayout will be read by default
    *  the others can be used in command: Xorg -layout layoutname
* Files - font and module path
* Monitor - one type of monitor
* Device - one video card, when more than one video card, BusID is needed
* Screen - bind video card with  monitor
* DRI - Direct Rendering Infrastructure (DRI)


## run level

### runlevel 3
* startx
    * xinit  - run .xinitrc in user home , otherwise default /etc/X11/xinit/xinitrc
        * run all scripts in /etc/X11/xinit/xinitrc.d
        * run .Xclients to start desktop environment or window manager
            * Xorg
            * connect X client applition to X
* because the user already logged in, not need to run display manager


### runlevel 5
* a X client application - display manager is launched to authenticate the user
    * GDM - GNOME display manager
    * KDM - KDE display manager
    * xdm - X Display manager , basic
* /etc/X11/prefdm - determin the prefered display manager by referencing /etc/sysconfig/desktop



Host:displayNumber:screen

displaynumber = x server instance


The value of DISPLAY is of the form host:displaynumber.screen and the default value set by practically all graphical environments is :0.0, which means the local computer, the X server instance 0, and SCREEN 0. 


https://virtualgl.org/Documentation/HeadlessNV
sudo nvidia-xconfig -a --allow-empty-initial-configuration --use-display-device=None \
--virtual=1920x1200 --busid {busid}










