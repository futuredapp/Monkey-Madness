# Monkey Madness - stress testing Android apps

##How it works
This set of scripts starts ADB monkey in Android device shell while locking your app to fullscreen to prevent unwanted results, monkey does random events generated from seed, so you can repeat same test again if you want. When your app crashes, log with all necessary information (seed, number of events, logcat from device...) is saved to desktop in folder with your app's package name.

##Requirements
1. Linux or macOS with Android Debug Bridge installed
2. Device/emulator with Android 5.0+ and usb debugging enabled
3. All files from this repo in same folder

##How to use
#####adb_test - run test
1. Turn on the device, connect it to computer and open app for testing
2. Start `adb_test` using terminal, you can specify optional arguments 
  - argument1 - number of input events (touch, scroll, swipe...) that monkey will attempt to perform
  - argument2 - seed for generating random events (could be useful to repeat test which failed)
3. Script will lock app to full screen to prevent monkey escape
4. Monkey will furiously tap screen and try to crash your app
5. If monkey crashed your app, crash log is saved to desktop in folder with your app's package name

Example: `adb_test 5000` - will start test with 5000 events, if app crash, log will be saved to desktop in folder with your app's package name.

#####adb_testloop - run multiple tests in a row
1. Turn on the device, connect it to computer and open app for testing
2. Start `adb_testloop` using terminal, you can specify optional arguments 
  - argument1 - number of tests to perform 
  - argument2 - number of input events (touch, scroll, swipe...) that monkey will attempt to perform in each test
  - seeds will be random
3. Your app will now be restarted
4. Script will lock app to full screen to prevent monkey escape
5. Monkey will furiously tap screen and try to crash your app
6. You see results of all tests, if monkey crashed your app, crash log is saved to desktop in folder with your app's package name.

Example: `adb_testloop 10 5000` - will start 10 consecutive tests each with 5000 events and random seed, if app crash, logs will be saved to desktop in folder with your app's package name.

#####adb_killmonkey - stop Monkey Madness
1. Use `adb_killmonkey`
2. Monkey is dead - log from interrupted test is saved to desktop in folder with your app's package name
 
##Warning
- Disable Messenger notifications when you use this tool! (If you want to prevent monkey from calling to random people and sending them messages.)
- Monkey won't stop its madness if you disconnect USB! You can kill it with CTRL+C or `adb_killmonkey` or by closing terminal.
- Keep in mind that monkey is unpredictable, it can send emails, delete files or worse if you let it (if it's possible inside your app). Always use debug versions of your apps to prevent dangerous actions.

##License

    MIT License
    
    Copyright (c) 2016 FUNTASTY Digital s.r.o.

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    urnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.
