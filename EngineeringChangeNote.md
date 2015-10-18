# Modifications to VBIT #
![https://lh4.googleusercontent.com/-RkN5ctI2_Zk/UBMM639KjNI/AAAAAAAALYk/2g43MP9R_uw/s676/IMAG1219.jpg](https://lh4.googleusercontent.com/-RkN5ctI2_Zk/UBMM639KjNI/AAAAAAAALYk/2g43MP9R_uw/s676/IMAG1219.jpg)

These modifications apply to the first VBIT circuit board. They must be done in order for the board to work.

1) The video sockets were phonos. These are not available any more. Replace these with BNCs. Mostly this will make it easier to hook up to other equipment. RS Part number 713-0802. You can fit this through the corner hole and one of the phono mounting points. Put a blob of solder on the leg of the phono. It won't bond to the board and will rattle around but at least it won't fall out. Then add wire links from the connector to the phono's empty signal pads.
![https://lh4.googleusercontent.com/-fIkbbgUZlV0/UBMNKhIbvzI/AAAAAAAALZE/b9c9ddd45QQ/s676/IMAG1225.jpg](https://lh4.googleusercontent.com/-fIkbbgUZlV0/UBMNKhIbvzI/AAAAAAAALZE/b9c9ddd45QQ/s676/IMAG1225.jpg)
![https://lh3.googleusercontent.com/-JZQVumSb2XE/UBMNNLWwwSI/AAAAAAAALZM/FmKJTtDoQ6g/s676/IMAG1226.jpg](https://lh3.googleusercontent.com/-JZQVumSb2XE/UBMNNLWwwSI/AAAAAAAALZM/FmKJTtDoQ6g/s676/IMAG1226.jpg)

2) Next the Serial RAM doesn't have a select signal. Also, the video encoder has a reset signal that we don't need. So we swap these over. Do not fit [R8](https://code.google.com/p/vbit/source/detail?r=8). Instead add a wire-wrap wire on the pad connected to the serial ram to pin 4 of the Header. That is now the RAM select. Break the PCB trace coming from header pin 4 then link that to Vcc. That leaves the encoder permanently enabled.

3) The I2C doesn't have proper pullups. The AVR doesn't have enough so it can't run very fast. The solution is to fit proper pull-up resistors. Pins 7 and 8 of the header are the I2C Data and Clock. Tack 3k3 resistors onto these pins underneath the board. Wire the other end of the resistors to Vcc.
![https://lh3.googleusercontent.com/-wP4izLU1ri0/UBMM-NpYPII/AAAAAAAALYs/VGBT1Y0aDdA/s508/IMAG1221.jpg](https://lh3.googleusercontent.com/-wP4izLU1ri0/UBMM-NpYPII/AAAAAAAALYs/VGBT1Y0aDdA/s508/IMAG1221.jpg)
4) The power doesn't have enough decoupling. Find a 100uF surface mount capacitor and scrape the solder resist from a convenient place on Vcc and ground. Tack the capacitor onto the copper.

5) The pins on header P6 don't match the processor too well. When you fit the header leave off pins 9 and 10.
![https://lh4.googleusercontent.com/-uPVsLxab5uI/UBMNCRRE68I/AAAAAAAALY0/1nmQI8blXs4/s676/IMAG1223.jpg](https://lh4.googleusercontent.com/-uPVsLxab5uI/UBMNCRRE68I/AAAAAAAALY0/1nmQI8blXs4/s676/IMAG1223.jpg)

6) You can also leave off pins 11 and 12 too unless you want to use this for power.

7) Make your own arrangements to connect power to the unit. Remember that it is 3.3VDC. This conveniently comes from the processor board. A wired link will do the trick. Connect to a convenient location. I chose the power input side of L2 and the ground side of C12. The other end of the cable can use a Takbro or a connector from inside a PC. Put a two pin header on the CPU board to plug the power in.
![https://lh4.googleusercontent.com/-fq0qRelSrO0/UBMNHyOmACI/AAAAAAAALY8/BxbACU9svbk/s676/IMAG1224.jpg](https://lh4.googleusercontent.com/-fq0qRelSrO0/UBMNHyOmACI/AAAAAAAALY8/BxbACU9svbk/s676/IMAG1224.jpg)

8) The CPU board on the MT-X1 needs headers. Put a 2x5 header on C0/C1 to D0/D1. If you want to use JTAG then add that header too. Add a two pin header across 3.3V and GND, the one next to D6/D7 is the most convenient.