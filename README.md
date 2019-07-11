<div align="center"><h1>WIFICFG</h1></div>
<div align="center"><h2>For ESP8266/ESP32</h2></div>
<div align="center">Powered By <a href="https://github.com/Mashiro-Sorata">Mashiro_Sorata</a></div>

---

## Content
0. [Introduction](#u0)
1. [Start](#u1)
2. [Details](#u2)
3. [Download](#u3)
4. [License](#u4)

---

<h2 id="u0">0. Introduction</h2>

__WIFICFG__  is a MicroPython module for ESP8266 or ESP32 device. WiFi could be set without writing the _SSID_ and _Password_ to the code.

Multiple WiFi configuration could be saved to Json file. So when the network environment changes, it will work fine as long as this WiFi configuration in file.

But how to configure the Json file? Do I need to edit it manually? Don't worry about it!

You only need to connect to the hotspot named "_ESP-WIFICFG_" (password:_3.1415926_), access to _192.168.4.1_ in the browser, and then configure it. WiFi that has been successfully connected will save to Json file automatically.

<h2 id="u1">1. Start</h2>

Download __WIFICFG.py__ to your environment.

```PYTHON
from WIFICFG import WiFi
WiFi.LOG = False
wifi = WiFi()
wifi.auto_run() #or wifi.auto_run("your_ssid", "your_password")
```

### Connect once

```PYTHON
from WIFICFG import WiFi
wifi = WiFi()
wifi.connect("your_ssid", "your_password")
```

<h2 id="u2">2. Details</h2>

```PYTHON
class WiFi

----main attribute:
    ----WiFi.LOG: Print status if WiFi.LOG == True

----main method:
    ----__init__(self, file="WIFICFG.json"):
        Parameter (file) is the path where the Json file saved.

    ----auto_run(self, ssid=None, passwd=None, retry=0):
        (retry) is the retry times when connection failed.
        method auto_run(ssid, password) will try connecting to ssid that gived in function firstly.
        If connection failed, try connecting to WiFi in Json file.
        If connection failed again, try configuring WiFi with web.

    ----connect(self, ssid, passwd):
        Connect to ssid once.
        return True if successful else False.
        Update the Json file every time the connection is successful.

    ----load_cfg(self):
        Load Json file.
        return dict(ssid1=passwd1, ssid2=passwd2, ...).

    ----update_cfg(self, ssid, passwd):
        Update Json file.

    ----scan(self):
        Scan WiFi and sort by rssi.
        return list(ssid1, ssid2, ...)

    ----log(self, *args, **kws):
        self.log(info) = print(info) if WiFi.LOG == True else print(end="")

    ----get_cfg_from_web(self):
        while True:
            get ssid and password from web
            if self.connect(ssid, password):
                break
```

<h2 id="u3">3. Download</h2>

[Source code](https://github.com/Mashiro-Sorata/ESP-WIFICFG/archive/v1.0.zip)

<h2 id="u4">4. License</h2>

[MIT License](https://github.com/Mashiro-Sorata/ESP-WIFICFG/blob/master/LICENSE)
