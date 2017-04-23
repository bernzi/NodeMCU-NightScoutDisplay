# NodeMCU-NightScoutDisplay
Display Nightscout data using a cheap NodeMCU and OLED display (instead of using an old phone or tablet).<br />
Displays: NS BG with direction arrow, yellow hihi,high,low,lolo alarms, stale data indication(value crossed out if NS data is old), displays 'Loading' when data is old due to repeated wifi connection attempts

# Components/Wiring
* Display: [0.96" Inch Yellow Blue I2c IIC Serial Oled](https://www.amazon.com/Diymall-Yellow-Serial-Arduino-Display/dp/B00O2LLT30)
* WIFI NodeMCU: [NodeMCU LUA ESP8266](http://www.ebay.co.uk/itm/NodeMCU-LUA-WIFI-Internet-Development-Board-Based-on-ESP8266-/291505733201?hash=item43df187e51:g:iikAAOSwHPlWeoBr)
* MicroUSB Cable
* Wiring:<br />
** D1 on WIFI NodeMCU -to- SDA on Display<br />
** D2 on WIFI NodeMCU -to- SCL on Display<br />
** 3V3 on WIFI NodeMCU -to- GND on Display<br />
** GND on WIFI NodeMCU -to- VCC on Display<br />
** MicroUSB(powered/plugged into wall or computer, ect) -to- WIFI NodeMCU USB port

# Directions
1. Download this repo [NodeMCU-Wixel repository](https://github.com/shelsgit/NodeMCU-NightScoutDisplay) and extract the files 
2. Open the NightSout.lua file: line 20, and change any other constants you want to change in the "--constants" section (starting on line 19)(and save file)
3. Open the init.lua file and enter your WIFI info (ip, netmask, gateway, wifissid, wifiPassword) (and save file)
4. Wire together (solder or use breadboard) the Display and WIFI NodeMCU (see 'Components/Wiring' section above)
5. Flash the firmware to your NodeMCU, using [NodeMCU-flasher](https://github.com/nodemcu/nodemcu-flasher):
   * Connect the NodeMCU to your computer (using the MicroUSB)
   * Open the NodeMCU-flasher 
   * In the Config tab:
     * Browse to the firmware file (from this repo, which you downloaded in step1: /NodeMCU-Firmware/nodemcu-master-14-modules-2017-04-08-22-15-36-integer.bin)
     * Set Offset to 0x00000
   * In the Operation tab:
     * Select the COM Port (that your NodeMCU is connected to)
     * Click the Flash button (Wait until finished, then close NodeMCU-flasher)
6. Upload .lua files onto the NodeMCU using [ESPlorer](http://esp8266.ru/esplorer/):
   * Connect the NodeMCU to your computer (using the MicroUSB)(if not already)
   * Open the ESPlorer Program 
   * Select COM port
   * Set Baud rate to 115200
   * Click Open (you'll probably see an error that you can't communicate)
   * Click the reset button on the NodeMCU
   * Click the 'Upload button' and upload the (2) lua files (from this repo, which you downloaded in step1: /NodeMCU-lua/NightScout.lua and /NodeMCU-lua/init.lua)
   * Click the reset button on the NodeMCU (you should see "WiFi connection established, IP address: " and "You have 5 seconds to abort", and more ongoing scrolling messages afterwards to know it's working, and ready to unplug and use wherever you want to put it that has a wifi connection)

# Disclaimers and Known Issues
This project is for research only.  Don't use it for any medical decisions.<br />
This is my first first time programming anything real from scratch.  I'm sure it can use improvements!  It seems to work ok (but includes a workaround to reset the nodeMCU after continued failed https connection attempts, and you'll see 'Loading...'!)

# Acknowledgements
This project relies on [The Nightscout Project](http://www.nightscout.info/) - Thanks to them for helping so many people - Please consider [donating to NightScout](http://www.nightscoutfoundation.org/donate/)<br />
This project works well with [NodeMCU-Wixel](https://github.com/MrPsi/NodeMCU-Wixel/blob/master/README.md) - No need to carry a receive and phone (or display!) around the house with you<br />
Instead of using this project, you could display your Nightscout data using an old phone or tablet - [Nightscout Remote Monitor](https://github.com/nightscout/cgm-remote-monitor), a nice large colorful display with arrow instead: [Nightscout Remote Monitor](https://github.com/sarahspins/cgm-remote-monitor/tree/dev/static)<br />
Instead of using this project, you could display your Nightscout data using arduiono and Adafruit hardware - [Ruuddotorg NS Display](https://github.com/ruuddotorg/nightscout-display)<br />


