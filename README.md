This is a fork of JeeLab & Adafruit's real time clock library for Arduino modified to work with the ST M41T62 real time clock IC. Significant changes are to the square wave function and added alarm functions. See example sketches.

For details on using this library with an RTC module, see the guide at: https://learn.adafruit.com/ds1307-real-time-clock-breakout-board-kit/overview

To download. click the DOWNLOADS button to the right, and rename the uncompressed folder RTClib.

Place the RTClib folder in your *arduinosketchfolder*/libraries/ folder. 
You may need to create the libraries subfolder if its your first library. Restart the IDE.

2022 Update by Trey.
Added alarm get functions
- DateTime alarmGet(): Get the DateTime of the alarm set.
```
DateTime AlarmTime = rtc.alarmGet();
```
- int alarmEnabled(): Get 0/1 if an alarm is currently enabled.
```
int en = rtc.alarmEnabled(); // if there is no alarm enabled, like a first start, then we need to set one!
printf("alarmEnable: %d\n", en);
```
Check the OF bit.  Good to know on first start or if backup battery fails.
```
int rtc_OF = rtc.checkOF(); // Returns 1 if oscillator fail is set, 0 if not.
```
  
  
Added alarm functions
- alarmSet(DateTime): Sets alarm to desired time. Uses DateTime variable. Basically the same as adjust() but sets the alarm time instead.
- alarmRepeat(int): Returns or sets alarm repeat mode
  - 1: once per second
  - 2: once per minute
  - 3: once per hour
  - 4: once per day
  - 5: once per month
  - 6: once per year
- alarmEnable(bool): True/False to enable/disable alarm
