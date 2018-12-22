# eps01_relay

<h1>Overview</h1>
<p>This project allows a user to wire a relay into any exisiting 120-240v application and control the relay wirelessly via a simple web page. This functionality can be expanded to integrate with exisiting smart home devices, allowing for voice control of numerous devices.&nbsp;</p>
<h1>Hardware</h1>
<table>
<tbody>
<tr>
<td>
<h4>ESP8266 ESP-01 Module</h4>
<p>This project utilizes an ESP8266 ESP-01 WiFi module. Originally designed as a plug-n-play WiFi adapter for microcontrollers, the ESP-01 has gained a lot of attention as a simple/lightweight IoT solution. The ESP-01 is affordable, has a small form factor, and is relatively versatile. The ESP-01 has two IO pins that can be extremely useful, however this project does not use them to their fullest extent. The modules I used for this project can be found on Amazon.&nbsp;</p>
</td>
<td>
<p><a href="https://www.amazon.com/Makerfocus-ESP8266-Wireless-Transceiver-Compatible/dp/B01EA3UJJ4" target="_blank" rel="noopener">MakerFocus 4pcs ESP-01&nbsp;</a></p>
<p><img src="https://images-na.ssl-images-amazon.com/images/I/71Y5-uojO8L._SL1500_.jpg" width="150" height="150" /></p>
</td>
</tr>
<tr>
<td>
<h4>ESP-01 5v Relay</h4>
<p>In addition to the ESP-01 modules, this project utilizes a relay board designed for "simple integration" with the ESP-01 (Simple integration in theory). These boards come with a 120-240v relay, as well as a power controller allowing for 5v input (phone charger) and steps it down to the 3.3v required for the ESP-01 chip. It also has a reset button, which may or may not come in handy.&nbsp;</p>
<p><strong>Important Note:</strong></p>
<p>These boards require some modification to work properly (of course). The boards are cheaply made and cheaply designed. Thus you will need to bust out your handy soldering gun to make a fix. The problem is that the ESP-01 requires power to the 1st pin to boot into its executable code. If this pin is not brought up to 3.3v the ESP-01 will boot into programming mode and will not execute your code. To fix this, you need to solder a connection between the power pin and the programming pin (1st pin). This pulls the 1st pin up to 3.3v and allows the ESP-01 to execute your code. The following picture illustrates the modification</p>
<p><img src="https://www.da-share.com/wp-content/uploads/2018/02/WiFi-Relay-Module.jpg" alt="" width="569" height="484" /></p>
</td>
<td>
<p>&nbsp;<a href="https://www.amazon.com/WINGONEER-Esp8266-Esp-01S-Module-Project/dp/B07B9SMRHX/ref=sr_1_3?ie=UTF8&amp;qid=1545517436&amp;sr=8-3" target="_blank" rel="noopener">Wingoneer 3pcs ESP01 Relay Module</a></p>
<p><img src="https://images-na.ssl-images-amazon.com/images/I/61lc0FO91iL._SL1000_.jpg" width="150" height="150" /></p>
</td>
</tr>
<tr>
<td>
<h4>ESP-01 Serial Wireless Development</h4>
<p>The final piece of hardware required for this project is a way to upload code to your fancy new ESP-01 modules. This can be accomplished using a couple of different methods (google it). I chose to take what I thought would be the simpler path, the USB board. The board works great but again is cheaply designed/manufactured and thus requires some modification to get it up and running. A persistent problem with this project was the poorly designed hardware but, I am here to help save you some time. The development board suffers from the same issue as the relays but inversely. This time we want the board to boot the ESP-01 modules into programming mode, therfore we need to pull the GPIO0 pin down to tell the ESP-01 to enter programming mode. This can be accomplished with a simple switch between the power pin and programming pin (see example). With the switch installed you simply press it when inserting the usb into your computer, providing no power to GPIO0 and thus entering the chip into programming mode (<strong>NOTE:</strong> there will be a flashing blue light to tell you you're in programming mode).</p>
<p><img src="https://images-na.ssl-images-amazon.com/images/I/51GjmkgqrIL._SX425_.jpg" alt="" width="425" height="425" /></p>
</td>
<td>
<p><a href="https://www.amazon.com/diymore-ESP8266-ESP-01S-Wireless-Development/dp/B01J2UXXCA/ref=pd_sim_421_5?_encoding=UTF8&amp;pd_rd_i=B01J2UXXCA&amp;pd_rd_r=4eeada46-0638-11e9-a072-17decbef9670&amp;pd_rd_w=zvd0y&amp;pd_rd_wg=Sp0ru&amp;pf_rd_p=18bb0b78-4200-49b9-ac91-f141d61a1780&amp;pf_rd_r=ZYZMAB7DS9TEY79EP7P5&amp;psc=1&amp;refRID=ZYZMAB7DS9TEY79EP7P5" target="_blank" rel="noopener">DIYMORE ESP-01 Dev Board</a></p>
<p><img src="https://images-na.ssl-images-amazon.com/images/I/51GjmkgqrIL._SL1000_.jpg" alt="" width="150" height="150" /></p>
</td>
</tr>
</tbody>
</table>
<h1>Software</h1>
<h4>Required Packages</h4>
<ul>
<li>Arduino IDE</li>
<li>ESP8266 Arduino Toolkit</li>
<li>AI Thinker ESP8266 Firmware</li>
<li>ESP8266 Firmware Flash Tool (or use Linux)</li>
<li>Project Source Code</li>
</ul>
<h4>Arduino IDE</h4>
<p>Some assembly required, need to install 8266 toolset. <a href="https://www.instructables.com/id/Getting-Started-With-Esp-8266-Esp-01-With-Arduino-/" target="_blank" rel="noopener">Follow these instructions.</a></p>
<h4>Flash Firmware</h4>
<p>The ESP-01 modules from Amazon have a custom firmware, that does not play nice. Best to reflash with a better documented source. This will save you a lot of headache for this project as well as future projects. There are many firmware options for the ESP-01, I went with AI Thinker as it seemed to be fairly common and lightweight.</p>
<h4>Source Code</h4>
<p>Simple script that sets the system as a webserver and toggles one IO pin to switch the relay on and off.&nbsp;</p>
