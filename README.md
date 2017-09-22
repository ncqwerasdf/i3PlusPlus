# Introduction

**i3Plus+** is a custom firmware for the Wanhao Duplicator i3 Plus and its rebrands (Monoprice Maker Select Plus, Coccon Create). It offers a complete redesign of the touchscreen interface and new features.

Those features include:

* Complete menu rework
* Overhauled leveling assistant
* Overhauled move menu
* Live temperature graphs
* PID Autotuning menu
* Multiple preheat profiles with customizable temperatures
* Printing statistics

It is based on the [Marlin firmware](https://github.com/MarlinFirmware/Marlin) 1.1.4 instead of an old one like the original version from Wanhao.

This firmware is a fork of the work of [Silverquark](https://silverquark.github.io/i3PlusPlusSite/). The main difference is at the level of the LCD. The original version of Leo Lüker (Silverquark) uses dark green on a white background. This version uses orange and blue on a black background (i.e. has higher contrast):

![Starting Animation](https://raw.githubusercontent.com/andrivet/i3PlusPlus/master/assets/LCD.gif)

# How to flash the LCD

_**IMPORTANT**: Be sure to use a microSD card of maximum **8 GiB**. The LCD firmware has some problems when using a bigger SD card. Sometimes it works, sometimes not._

## Step 1 - Prepare a microSD card

You have two possibilities:

- Copy manually the files under LCD to the root of a SD card. The SD card **has** to be formatted with the following parameters: FAT32, 4096 bytes per cluster (i.e. 8 sectors). To format under Linux (and macOS with the `dosfstools` Homebrew package):

```
mkfs.fat -F 32 -n SD -s 8 -v /dev/disk2
```

Of course, replace `/dev/disk2` with the right value.

- Use the SD card dump I have prepared (in the Dumps directory). Just unzip the LCD30.zip file and use either `dd` (Linux, macOS) or [Etcher](https://etcher.io). For example with `dd`:

```
unzip LCD-i3plus-plus-1.0b4.raw.zip
sudo dd if=LCD-i3plus-plus-1.0b4.raw of=/dev/disk2 bs=64K
```

Of course, replace `/dev/disk2` with the right value.

## Step 2 - Install the new version

- Disconnect the printer from power
- Remove the two screws located on the front and loose the two M3 screws on the top

![Front panel](https://raw.github.com/andrivet/Wanhao-i3-Plus/master/assets/front-panel-screws.jpg)

- Remove the front panel carefully (don't break the flat cable)
- If you are lucky, you can insert the microSD card on the left of the panel (this is the case on the Monoprice clone)
- Otherwise, remove the four M3 screws and remove the cover
- Insert the microSD card in the slot

![Front panel](https://raw.github.com/andrivet/Wanhao-i3-Plus/master/assets/LCD-board-microSD.jpg)

- Turn on the printer (either by connecting it to power or by connecting the USB slot to the computer)
- The screen turns blue and then every image will appear one by one
- After around 2 or 3 minutes, the screen turns black
- Turn off the printer and remove the microSD card
- Re-assemle the front panel, do not forget the two M3 screws on the top
- Turn the printer on. You know have the new version of the LCD images

# How to flash the mainboard (printer firmware)

## With Cura

* Be sure your printer is in the list of **Printer**s (**Settings** &#x2192; **Printer**)
* Click on **Settings** &#x2192; **Manage Printer**
* Click on **Upgrade Firmware**, then on **Upload Custom Firmware**
* Select the **i3PlusPlus_XX.hex** file and click **Open**

## With other software

It is possible to flash the printer with other softwares such as :

* [Arduino IDE](https://www.arduino.cc/en/Main/Software)
* [OctoPrint](https://github.com/foosel/OctoPrint) with the [FirmwareUpdater plugin - devel branch](https://github.com/OctoPrint/OctoPrint-FirmwareUpdater/tree/devel)
* Etc.


# Known issues

* I have just change the bitmaps, not the metadata associated to them. In particular, I have not changed the colors of the variable texts. As a consequence, the list of files on the SD card is invisible (black text on black background). I will fix that.

# Future plans

* Fix the problem of the black text on black background
* Change some screens to display icons instead of text (for example for in the Filament menu)
* Change the fonts for the variable parts (LCD)
* Merge the latest version of Marlin

# Resources

- [DMT48270M043_05W Datasheet](http://www.dwin.com.cn/uploads/English%20Documents/Mini%20DGUS/DMT48270M043_05W_DATASHEET.pdf)
- [DWIN DGUS Display Development Guide version 4.3](http://dwin.com.cn/uploads/产品数据手册/DWIN%20DGUS%20DEV%20GUIDE_V43_2015.pdf)
- [DGUS SDK](http://www.dwin.com.cn/uploads/English%20Documents/DGUS_SDK.rar) - Windows only
- [DGUS firmware update](http://www.dwin.com.cn/uploads/产品数据手册/DGUS%20upgrade%20program%2020161024%20.rar). _WARNING: I have not yet tested it._
- [DWIN Documentations and softwares](http://dwin.com.cn/english/products/bt-72876584214435.html)

# Wanhao Firmware version 3

Wanhao has not yet released the sources of version 3.0 (even if it is required under GPL). I have ask them when they plan to release the sources. I am waiting...

I have made a modification of the LCD images for the Wanhao Firmware version 3.0. It is also available on [GitHub](https://github.com/andrivet/Wanhao-i3-Plus). The README contains information about the LCD and how to program it.

# Credits

* Based on [i3Plus+ by Silverquark](https://silverquark.github.io/i3PlusPlusSite/)
* Itself based on [i3Extra by nepeee](https://github.com/nepeee/i3Extra)
* Itself based on [Marlin Firmware](https://github.com/MarlinFirmware/Marlin)

# Disclaimer

I'm not responsible for any damage done to your printer or LCD. Use at your own risk.


# License

Marlin is published under the [GPL 3.0 license](https://github.com/COPYING.md). This fork is also released under the [GPL 3.0 license](https://github.com/COPYING.md).


