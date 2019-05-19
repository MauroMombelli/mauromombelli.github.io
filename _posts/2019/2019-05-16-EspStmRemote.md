---
layout: default
title: EspStmRemote
excerpt: Serial and programming STM32 over wifi
thumbnail: 
---

# {{page.title}}

The title says it all, really.  
  
I wrote a little script for ESP8266 (should work with minor modification on an ESP32 too) to add WiFi capability to any STM chip, code upload included.  
  
Unfortunately is not super smooth, especially on the upload side you need to do some magic, currently possible only in Linux (probably possibel in Windows too, but who use THAT?!)
  
I am building a remote car, controlled by a bluepill (STM32F103 fore less than 2€, shipping included) and I wanted to add simple serial communication so I could drive the car remotely. Unfortunately the ESP8266 does not have enough pin/interfaces for all I need.  
  
So the idea started easy, a simple serial to TCP using the ESP8266 and all would be done, right? right??  
  
But then I though, all STM32 chip has a Hardware Serial Bootloader; wouldn't be cool if the ESP would that for me, so I could upload new firmware in my remote car without moving my ass from the chair?  
  
So I added a little functionality to:  
 - reset the STM32
 - reset for upload the STM32 (serial in 115200 8E1 mode, set BOOT0, reset, relese BOOT0)
 - exit the upload mode (set the serial back to user baudrate 8N1 mode)
  
Of course i also add the ability to "program" the WIFi network into the ESP, so I added a little webpage.  
By default the ESP will create a network called "LESTO" with password "lestofante", and assign itself IP 192.168.0.123.  
  
You can connect to this network and change different parameter on the webserver, on TCP port 80 (http://192.168.0.123):
 - AP or client mode
 - SSID and pasword
 - connection timeout (if can't connect as a client, it will reset to AP mode with default conf)
 - DHCP enabled
 - ip/mask/gateway/
 - baudarate for the serial
   
 
The TCP to serial is runing on port 1234, so you can simply open netcat/telnet and connect to it. But it will accept only ONE connection at time!
Watherver you write here will be send on the serial, and the other way around.
  
the configuration server is on port 1235 (same limitation of one client at time only!) and accept the command:
 - `r` reset the STM32
 - `u` : enter upload mode (serial in 115200 8E1 mode, set BOOT0, reset, relese BOOT0)
 - `e` : exit upload mode (set the serial back to user baudrate 8N1 mode)
  
## How to connect
  
Easy peasy:  
 - the serial of the ESP to the serial of the STM
 - ESP GPIO4 to STM BOOT0
 - ESP GPIO5 to STM reset
  
As the STM work at 3.3v no special care is required; I assume you already set up the proper pull-up pull-down to make the ESP work properly.  
I am using a bluepill, it come with a 5v to 3.3v regulator, and has enough current for both chip. Your mileage may vary.  
  
## How to upload
  
ok, NOW come the hard part.  
we want to use stm32flash, an opensource tool, to upload.  
Unfortunately he want a Serial port.  
Fortunately we have socat, and we can run: `socat pty,link=virtualcom0,raw  tcp:192.168.0.199:1234`, this will create in the current directory a serial port `virtualcom0`.  
Unfortunately stm32flash will refuse to open the serial as it will fail a check.  
Fortunately with just commenting one line, it can be fix.  
Unfortunately the bug report is open since 12-2018 (https://sourceforge.net/p/stm32flash/tickets/94/).  
So for now the solution is to download, modify and compile stm32flash by yourself.
  
  
After you acquired your stm32flash, the procedure become:
 - close any application using the TCP serial on 1234
 - start socat serial
 - open a TCP connection to 1235 (if not already open) and send `u`
 - run `stm32flash` as you normally would: `stm32flash -b 115200 -w filename.bin -v -g 0x08000000 virtualcom0`
 - send on port 1235 `e` to reestablish the user serial settings
 - close sockat to free the serial-TCP for user application
