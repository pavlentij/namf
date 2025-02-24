NAMF-2020-38 (2021-08-20 )

NAMF-2020-38rc18 (2021-08-13 rev 9a35fdcdec50b2d84e13c0b1b70b1dccf6f45998)
* this is true pre-stable release. Since there are a lot of changes compared to NAMF-2020-37 this build is test before release (debug settings are identical as in stable, to get 100% there are no problems with fw) 

NAMF-2020-38rc17 (2021-08-06 rev a3233a0ad6292fa76d9246f99ad2b211aa0d2f01)
* BME280 support moved into new scheduler
* do not send data when no measurements

NAMF-2020-38rc16 (2021-08-04 rev 2bb1a84e9122198727466b2f739a712a2edc4694)
* support for older BMP sensors (BMP180/SHT31 will be used as BME280 replacement)
* changes to String handling in many places (concat instead of operator +=)

NAMF-2020-38rc15 (2021-07-31)
* tweaks with timings of SoftwareSerial
* SDS hardware watchdog - count total number of hw cycles

NAMF-2020-38rc14 (2021-06-19)
* display total and failed number of SDS readings
* display time from last update check
* corrected counting SDS failed/successful readings

NAMF-2020-38rc13 (2021-06-18)
* lucky thirteen (?)
* processing SDS packet using onReceive
* SDS serial buffer 20 bytes - should fit 2 responses
* disable interrupts on SDS serial TX

NAMF-2020-38rc12 (2021-06-17)
* good measurement SDS resets failed measurements counter 
* smaller buffer in SDS Serial
* compact timestamp when logging to console

NAMF-2020-38rc11 (2021-06-15)
* fixed version number in binary  
* hardware SDS restart after 3 missing measurements, not after first 

NAMF-2020-38rc10 (2021-06-15) (typo in version number, binary built with 39 not 38...)
* new SDS code, moved some functionality to separate class, work in progress 
  to get nonblocking full implementation SDS communication protocol, not just toss
  some commands to SDS...
* support for hardware watchdog/restarter for SDS

NAMF-2020-38rc9 (2021-06-07)
* old (2019 line) code for sending SDS commands (diagnosing SDS problems)

NAMF-2020-37a (2021-06-04)
* collect SDS statistics when checking for an update

* NAMF-2020-38rc8 (2021-06-04)
* fixed update check interval for beta channel

NAMF-2020-38rc7 (2021-05-26)
* add mDNS TXT field 'manufacturer'
* when checking for update report number of SDS readings

NAMF-2020-38rc6 (2021-05-20)
* send TXT record with ID key (NAM-XXXX), to allow Home Assistant to discover NAM if host name is set to different than NAM-XXXX
* SHT3x sensor used as temp/humidity sensor (not in HECA) can display measurements on LCD
* rewrite display interface in new scheduler - more simple code, new scheduler displays now both on LCD and OLED
* SPS30 FW version displayed on /status page

NAMF-2020-38rc5 (2021-05-17)

* with new SDS code result -1 (no data from SDS) is being reported to Influx (not to other APIs) like it was with old code in 37rc3 

NAMF-2020-38rc4 (2021-05-16)

* old HECA/SDS011 enable checkbox enables both sensor and LCD display - to mimic old behaviour
* subsystem list on /values page is now complete (SDS011 name was missing)

NAMF-2020-38rc3 (2021-05-14)

* if HECA old_style was enabled - force enabling new HECA subsystem. No reconfiguration need after upgrade

NAMF-2020-38rc2 (2021-05-14)

* HECA is now under new scheduler
* HECA reports duty cycle (how long heater was enabled during current measurement period)
* SDS011 now display header on LCD 20x4
* sending hostname to Influx was lost during merge - reenabled

NAMF-2020-38rc1 (2021-05-10)

* aim to finish SDS readings 2 sec before sending time - should not catch SDS during collecting data on sending time
* log when procedure takes longer than 1s
* use SoftwareSerial library bundled with Arduino Core
* added uptime to data.json (in seconds)
* on /values page there is a link to graphs for given sensor on madavi.de

NAMF-2020-37 (2021-04-27)

* Merged all beta releases (37rcX)

NAMF-2020-37rc5 (2021-04-15)
* better translation on config page (new scheduler)
* use subsystem names on /status pages
* fixed Network Watchdog - do not toggle status when saving config on enabled WTD

NAMF-2020-37rc4 (2021-04-14)
- send to influx hostname (fs_ssid) 

NAMF-2020-37rc3 (2021-03-30)
- when sending to Infux send also firmware version and update channel
- if SDS is enabled always send result to influx. This will send -1 instead skipping reading - but **only** for influx. Other APIs won't get -1 (behavior won't change)
- due to misconfiguration of build environment this release will use proper SoftwareSerial version (previous binaries were built against older version)

NAMF-2020-37rc2 (2021-03-28)
- support for NAM LED BAR with brightness regulation
- status/debug info moved from /values to new page /status
- dump seen I2C addresses on status page
- NTP server is selected based on firmware language

NAMF-2020-37rc1 (2021-03-22)
- do not send wrong data when WINSEN MHZ14A is enabled, but not present
- getting time from NTP fixed

NAMF-2020-36 (2021-03-22)

Merged NAMF-2020-36rc3 and previous

NAMF-2020-36rc3 (2021-02-20)
- new names for JSON variables in SHT3x

NAMF-2020-36rc2 (2021-02-17)
- Sending data to LuftDaten/SensorCommunity from SPS30 and SHT3x

NAMF-2020-36rc1
- Espressif8266 platform upgrade (2.6.2) - Arduino Core 2.7.4

NAMF-2020-35 (2021-01-25)

Merged NAMF-2020-35rc5:

* Winsen MHZ14A support moved to new scheduler
* SPS30 and MHZ14A can now display results on LCD
* fixes to config pages (new scheduler)
* `upload_config.ini` allows to setup custom Platformio options for developers and not interfere with main .ini file

NAMF-2020-35rc5 (2021-01-20)
- fix for two or more sensors having access to display 

NAMF-2020-35rc4 (2021-01-19)
- enabling/disabling LCDs for Winsen and SPS30 should now work
- changed  SPS30 20x4 screens layout a bit

NAMF-2020-35rc3 (2021-01-16)
- MHZ14A support moved to new scheduler
- display CO2 concentration on LCD

NAMF-2020-35rc2 (2021-01-08)
- display data on LCD for sensors managed by new scheduler
- support for custom upload options like OTA password (see platformio.ini, search for uplaod_options.ini)
- fixed error when enabling sensors managed by new scheduler (it was toggle more than enable)
- more readable sensors description on config page (new scheduler)

NAMF-2020-35rc1 ()
- Dont broadcast OTA service, until it is not enabled via /ota
- You can use upload_opts.txt file to provide upload password (see `platformio.ini`)

NAMF-2020-34 (2020-12-18)
- new stable release, includes all 34rcx from beta

NAMF-2020-34rc5 (2020-10-08)
- bigger memory buffer for JSON data
- send GPS_date and GPS_time to influx as strings

NAMF-2020-34rc4 (2020-10-08)
- fix for core dump when enabling Network Watchdog

NAMF-2020-34rc3 (2020-09-12)
- don't show empty SHT3x results when sensor is not enabled

NAMF-2020-34rc2 (2020-09-12)
- support for SHT3x sensor as temperature/humidity (fixed 0x45 I2C address, since 0x44 is being used by HECA)
- a bit more separation between forms on config page

NAMF-2020-34rc1 (2020-08-31)
* merged PR#16 - allows upload code via OTA, for dev purposes, requires to have password

NAMF-2020-33 (2020-08-22)
* stable relase based on rc3

NAMF-2020-33rc3 (2020-08-21)
* SPS30 - added missing 0.5 particles count reading 

NAMF-2020-33rc2 (2020-08-14)
* version bump to check autoupdate software option
* increased update check interval from 1h to 6h
* enabling SPS30 w/o connected hardware should not stop whole sensor
* use UTF-8 explict when open language files (required on Windows to compile) 

NAMF-2020-33rc1 (2020-08-13)
* respect autoupdate option

NAMF 2020-32 (2020-08-01)
* Updated missing translations in Polish

NAMF 2020-31 (2020-07-08)
* new scheduler
* SPS30 support (high precision particular matter sensor from Sensirion)
* network watchdog - restart sensor if can not ping given IP for three times in row (10 pings each time)

NAMF 2020-30 (2020-06-02)
* CPU clock boosted to 160 MHz
* display info about free SPIFFS and CPU freq on start (Serial)
* First green LED on LED bar now starts from 0.1 instead 1.
* Option to set WiFi PHY Mode to extend range

NAMF 2020-29 (2020-05-18)
* in case of crash, stack dump will be saved in /stack_dump file on SPIFFS
* new url /stack_dump shows latest stack dump

NAMF 2020-28 (2020-04-24)
* option to disable displaying WiFi SSID/IP addr
* code cleanup - moved some display functions to separate files

NAMF 2020-27 (2020-04-05)
* fixed malformed JSON in /data.json (merged PR#5)

NAMF 2020-26 (2020-03-17)
* added I2C RGB LED Bar support

NAMF 2020-25 (2020-03-09)
* merged PR#4 with Logger differentiation based on Luftdaten code
 
NAMF 2020-24 (2020-03-08)
* added Content-Length to headers when sending data to API. Should fix issue #3 

NAMF 2020-23 (2020-03-3)
* technical release to make sure binaries on update server correspond to code in GH

NAMF 2020-22 (2020-03-3)
* check for updates every hour
* don't check for update every time when sending data 

NAMF 2020-21 (2020-02-27)
* default Winsen MH-Z14A CO2 range set to 2000 ppm
* Winsens averaging function should not lower result in first measurement
* polish fw can be built with build timestamp in page header (create .add_build_time empty file in root directory)

NAMF 2020-20 (2020-02-22)
* bugfix in Winsen CO2 averaging function

NAMF 2020-19 (2020-02-22)
* both BME280 and HECA should not send to API results when communication error (still -128°C as temperature in WWW intreface)
* changed BME280 library to fork with fixed hangs. Waiting for AF to include changes
* (almost) all logs on Serial are with timestamps
* don't send HECA logs to Luftdaten API
* support for CO2 sensor - Winsen MH-Z14A, connect it to D6/D5 instead of GPS. So CO2 sensor or GPS no both  

NAMF 2020-18 (2020-02-21)
* we return to 80MHz on ESP8266
* VTables in DRAM
* bugfixes, hope to get more reliable

NAMF 2020-17 (2020-02-19)
* uptime is nice formatted not just seconds
* outputPower can be adjusted also in AP mode

NAMF 2020-16 (2020-02-19)
* hostname for DHCP server
* interface changes: removed map link, utf-8 icons in main menu
* interface changes: removeConfig moved to bottom, save & restart is now red, more icons
* config AP SSID is now mDNS and DHCP hostname. Using UTF-8 special chars and dot (".") may mess with propper mDNS resolving.
* disabled HTTP 1.1 support in HTTP client
* removed unused links /generate_204 & /fwlink
* readme update
* lang files update
* sensor name based on AP SSID visible in header
* removed int_templ.h 

NAMF 2020-15 (2020-02-18)
* /forceUpdate will now work with custom URL, until now it worked only with default
* new config option - WiFi TX output power

NAMF 2020-14 (2020-02-17)
* HECA support moved to src/sensors/heca
* started move webserver functions to separate file
* stopped software version spoofing

NAMF 2020-13 (2020.02.17)
* fix for garbage auth data when sending to Luftdaten/Madavi

NAMF 2020-12 (2020.02.17)
* allow to disable character LCD
* remove config button is now orange to avoid confusion with restart button
* fixed basic auth when sending to influx and custom API

NAMF 2020-11 (2020.02.16)
* moved to dynamic definition of LCDs (both character and graphical) Less code, less memory
* since only one char LCD is supported in given config HTML was changed to dropdown on config page
* memory stats are being collected in more logic way (max/min values measured at end of each loop)
* WiFi password is visible in input field when sensor is being first time configured. When already configured sensor is booted in AP mode, password is not shown (thus saving form with empty field will remove password from config)  

NAMF 2020-10 (2020.02.14)
* new core 2.6.3
* added Core & SDK version to measurements page
* more internal parameters (heap frag, free mem etc) is being sent to Influx
* a lots love with st Valentine's day!

NAMF 2020-9 (2020.02.13)
* /data.json now returns also measurements count
* added MaxFreeBlockSize and HeapFragmentation to influx and diagnostics (on current values pages)
* added Uptime, Reset Reason, Free Memory and Heap Fragmentation to measurements page

NAMF 2020-8 (2020.02.11)
* mDNS brought back
* to influx sensor sends also amount of free memory
    
NAMF 2020-7 (2020.02.10)
* memory leak in sendData fixed
* new target with stage boot firmware (migration from old firmware with Flash 1:3)

NAMF 2020-6
* SSL/plain connection fixes

NAMF 2020-5
* updating libraries and core to most recent
* SSL seems to be working 

NAMF 2020-4
* forceUpdate - page to force update from custom URL
* provide way to display current config as JSON and upload it later to sensor (/configSave.json)

NAMF 2020-3
* display on webpage first reading from SDS011 (collected on POST)

NAMF 2020-2 (2020-01-25)
* OTA update working

NAMF 2020-1
* Firmware separated from Luftdaten project structure
* New flash layout (2m for code, 2m for SPIFFS). 

