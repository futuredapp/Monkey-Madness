# Monkey Madness - stress testing android apps

##How it works
This set of scripts starts adb monkey in android device shell while locking your app to fullscreen to prevent unwanted results, monkey does random events generated from seed, so you can repeat same test again if you want. When your app crashes, log with all necessary information (seed, number of events, logcat from device...) is saved to desktop in folder with your app's package name.

##Requirements
1. Linux or macOS with Android Debug Bridge installed
2. Device with Android 5.0+ and usb debugging enabled
3. All files from this repo in same folder

##How to use
#####adb_test - run test
1. Turn on the device, connect it to computer and open app for testing
2. Start adb_test using terminal, you can specify optional arguments 
  - argument1 - number of input events (touch, scroll, swipe...) that monkey will attempt to perform
  - argument2 - seed for generating random events (could be useful to repeat test which failed)
3. Script will lock app to full screen to prevent monkey escape
4. Monkey will furiously tap screen and try to crash your app
5. If monkey crashed your app, crash log is saved to desktop

Example: "adb_test 5000" - will start test with 5000 events, if app crash, log will be on desktop

#####adb_testloop - run multiple tests in a row
1. Turn on the device, connect it to computer and open app for testing
2. Start adb_testloop using terminal, you can specify optional arguments 
  - argument1 - number of tests to perform 
  - argument2 - number of input events (touch, scroll, swipe...) that monkey will attempt to perform in each test
  - seeds will be random
3. Your app will now be restarted
4. Script will lock app to full screen to prevent monkey escape
5. Monkey will furiously tap screen and try to crash your app
6. You see results of all tests, if monkey crashed your app, crash log is saved to desktop

Example: "adb_testloop 10 5000" - will start 10 consecutive tests each with 5000 events and random seed, if app crash, logs will be on desktop

#####adb_killmonkey - stop Monkey Madness
1. Use adb_killmonkey
2. Monkey is dead - log from test is saved to desktop
 

