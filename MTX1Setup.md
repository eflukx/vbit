# MT-X1 Dev Board #

The MT-X1 board replaced the old development board in June 2011. The hardware is a little different.

# Hardware Details #

You can get away with using a mini USB cable to program and run the board. You will need a Micro SD card to store teletext pages on. My local shops only stock 2GB cards and this is fine.
The headers required on the MT-X1 are shown on https://picasaweb.google.com/peterk.vt80/VBIT#
# Software Details #
Go to the Mattair MT-X1 website and download everything on that page!
http://xmega.mattair.net/code.html
If you are using a Windows PC then plug the board in using the USB. The driver should start to install. Point the driver at your downloaded INF file MT\_X1.INF.
Start Hyperterminal and configure a new connection. The highest COM number is likely to belong to the board.
Linux is a bit easier. The device normally pops up as /dev/ttyACM0 and you can use miniterm to connect.
When you connect it should say "MT-X1 XMEGA Demo Program".
You should be able to run through the pre-installed demos.
# Installing VBIT #
VBIT connects to the dev. board by a data cable and a power cable.
  * Put a 2x5 header at port pins C0 to D1.
  * Put a 1x2 header in any slot marked GND 3V3. The one on the end of  Port D is most convenient.
  * If you have a JTAG programmer like AVRDRAGON or AVR JTAGICE MkII then fit a 2x5 header in the JTAG port.
  * You will also want to fit a proper crystal. Use solder wick to open solder jumper J7 and fit a 16MHz crystal into [R0](https://code.google.com/p/vbit/source/detail?r=0) and [R1](https://code.google.com/p/vbit/source/detail?r=1). If you don't fit and configure the crystal then it will still work! But only if you choose the "s" level of optimisation.

You will need to download Atmel AVR Studio 4. Other versions may work, that is the only one that I have tried. Connect it up and try to get the terminal running.
Get Hyperterminal running. If you don't have Hyperterminal then copy the relevant files from an XP computer and run it on your Vista or Windows 7 box.

On the MicroSD card you need an Onair folder with pages.all and mag1.lst. This is your teletext service.

# About the MT-X1 #
The software supplied by J Mattair needs a few tweaks:
**Atmel's I2C has an addressing problem.** The 16MHz crystal needs configuring.
**The blocking USB routines need to be unblocking.
If anyone needs this then please write and I'll zip the entire project complete with all the tweaks.**


TODO:
How to make a **short** 10 way ribbon cable and a decent rated power cable.
The VBIT header is 2x6 but you should only fit a 2x5 header. Place it so that the two holes nearest the middle of the board are left unconnected. Or cut them off if you have already soldered pins in this location. Pin 1 is now the top left pin.