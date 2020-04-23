# SPI-Playground

This repository is mainly meant as a companion for a JetsonHacks article about SPI. Requires JetPack 4.3+ (L4T 32.3.1+).

Directions here are for a Jetson Nano running JetPack 4.3
<h3>Enable SPI</h3>
In the default configuration on all Jetsons in JetPack 4.3, several of the GPIO pins which can be used to represent specialized functions (SFIO) are configured as GPIO. The tool jetson-io provides a user interface to help configure the pins.

jetson-io builds a device tree overlay from user input, and applies it to the device tree. In version JetPack 4.3 (L4T 32.3.1), there are a couple of issues. Here is the documentation page:

https://docs.nvidia.com/jetson/l4t/index.html#page/Tegra%2520Linux%2520Driver%2520Package%2520Development%2520Guide%2Fhw_setup_jetson_io.html%23wwpID0E0JE0HA

From the instructions, first fix the __init__ functions:
<blockquote>
$ sudo find /opt/nvidia/jetson-io/ -mindepth 1 -maxdepth 1 -type d -exec touch {}/__init__.py \;
</blockquote>

If you are using a Jetson Nano and JetPack 4.3, there is an additional step needed that is not documented in the above document. If you are using a Jetson Nano, copy the dtb file for the Nano to /boot/dtb
<blockquote>
$ sudo mkdir /boot/dtb<br>
$ sudo cp -v /boot/tegra210-p3448-0000-p3449-0000-[ab]0[012].dtb /boot/dtb/
</blockquote>

Now you are ready to run to jetson-io tool. From a Terminal (the window should be maximized to be able to see the entire menu context):
<blockquote>
$ sudo /opt/nvidia/jetson-io/jetson-io.py
</blockquote>

You will now be able to configure the SPI ports. Remember to save your assignments, and reboot the machine to take effect.
<h3>Examples</h3>
In the 'examples' folder, there are sample Python scripts to run an Adafruit ST7735 based display.For how to use the examples, see the 'README.md' file in the examples folder. 


<h3>Notes</h3>
<b>April, 2020</b>
<ul>
  <li>JetPack 4.3, L4T 32.3.1</li>
  <li>Jetson Development Kits</li>
  <li>Tested on Jetson Nano Development Kit</li>
 </ul>
