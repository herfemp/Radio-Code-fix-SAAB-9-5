# Radio-Code-fix-SAAB-9-5
Radio code fix for SAAB 9-5, designed for ESP8266. For hardware and software dependencies see the other repos
Installation and use of Radio Code fix based on CANBus messages on I-BUS (IIRC colorss of canH and canL are switched between P and I bus)<br />

Installation of Arduino IDE and the extra libraries<br />

Download Arduino and install the stable version of Arduino IDE for your operation system: https://www.arduino.cc/en/Main/Software Accept all standard setting and install all of the required add-ons<br />
Start Arduino<br />
Open the attached sketch (.ino)<br />
In File>Preferences find the empty field called “Additional Boards Manager URL” and paste this link there: <br />http://arduino.esp8266.com/stable/package_esp8266com_index.json<br />
Open board manager from Tools>Board:Arduino/Genunino Uno>Boards Manager<br />
Search for esp8266, it will find only one result, click install<br />
Go to https://github.com/Seeed-Studio/CAN_BUS_Shield, click download or clone and download the zip file. Then extract it here: <br />C:\Users\YourUserNmae\Documents\Arduino\libraries<br />
Replace the mcp_can.h and mcp_can_dfs.h files in C:\Program Files (x86)\Arduino\libraries\CAN_BUS_Shield-master with the ones provided in this project<br />
Go to Tool>Board and select NodeMCU 1.0<br />
Go to Tool>Board and select the appropriate com port<br />
Go to Tool>Board and select the highest upload speed<br />
Restart Arduino IDE<br />
Open the Sketch and click the upload button (right arrow). If everything went well it will start to flash the logger.<br />

Make sure you also change the 50 kbps entry in C:\Users\USERNAME\Documents\Arduino\libraries\CAN_BUS_Shield-master\mcp_can_dfs<br />

#define MCP_8MHz_50kBPS_CFG1 (0x03) //actually 8MHZ 47.619kBPS<br />
#define MCP_8MHz_50kBPS_CFG2 (0xBB) //actually 8MHZ 47.619kBPS<br />
#define MCP_8MHz_50kBPS_CFG3 (0x07) //actually 8MHZ 47.619kBPS<br />
<br />
and <br />
#define MCP_16MHz_50kBPS_CFG1 (0x06) //actually 16MHZ 47.619kBPS<br />
#define MCP_16MHz_50kBPS_CFG2 (0xBE) //actually 16MHZ 47.619kBPS<br />
#define MCP_16MHz_50kBPS_CFG3 (0x07) //actually 16MHZ 47.619kBPS<br />
<br />
Because SAAB I-bus is not exactly 50kBPS. For the rest follow my instructions on github for T7logger and steering wheel buttons projects. The code is for ESP8266, but should work on other arduino flavors with very slight modifications.
