# Readme

The Debian Package led-drv-f4-220
----------------------------

This is a linux driver for LED status lights of the TerraMaster F4-220.
It was created looking at the binary of the driver module from TerraMaster.
I later found there is now a GPL source version provided by TerraMaster at
https://www.terra-master.com/code/led_drv_1800.c .


Originaly forked from https://github.com/stroyan/led-drv-f4-220.
Great work from, Mike Stroyan <mike@stroyan.net>  Mon, 13 Jan 2020 15:10:29 -0700

Modified by me for it to wotk with OpenMediaVault 5, and latest kernel (5.6)
 -- Joao Amaro <joao.amaro@gmail.com>  Sun, 19 Jul 2020 18:39:47 

  
# What is working:

This is a kernel module.
It allows to change the colors of the front leds on Terramaster F4-220.
It creates a char device in /dev/leds that you can write into it, and change de colors of the LEDS.
They do not track the current usage of the disks (maybe in the future, who knows :) )

For the hard drives leds you can change the colors to: Green, Yellow, Red
For the LAN led you can change the colors to Green.
  
# Install:
Download this repo to your terramaster, and compile
That's it.

```bash
cd led-drv-f4-220
make
make install
```

After make install you can load module with
```bash
modprobe leds-f4-220
```

If you want to load it at boot time
```bash
echo "leds-f4-220" >> /etc/modules
```

# How to use
Just echo the desired state to /dev/leds

Permitted states are:

   HD1_off    - To disabled HD1 led

   HD1_green  - To set HD1 led green

   HD1_yellow - To set HD1 led yellow
   HD1_red    - To set HD1 led red

   HD2_off    - To disabled HD2 led
   HD2_green  - To set HD2 led green
   HD2_yellow - To set HD2 led yellow
   HD2_red    - To set HD2 led red

   HD3_off    - To disabled HD3 led
   HD3_green  - To set HD3 led green
   HD3_yellow - To set HD3 led yellow
   HD3_red    - To set HD3 led red

   HD4_off    - To disabled HD4 led
   HD4_green  - To set HD4 led green
   HD4_yellow - To set HD4 led yellow
   HD4_red    - To set HD4 led red

   LAN1_off   - To disabled LAN led
   LAN1_on    - To set LAN led green

Examples:

```bash

echo -n HD1_green > /dev/leds
echo -n HD2_yellow > /dev/leds
echo -n HD3_red > /dev/leds
echo -n HD4_off > /dev/leds
echo -n LAN1_on > /dev/leds
```

# Contact
joao.amaro@gmail.com

# License


