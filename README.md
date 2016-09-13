# Monkey Madness - stress testing Android apps

##How it works
This set of scripts starts ADB monkey in Android device shell while locking your app to fullscreen to prevent unwanted results, monkey does random events generated from seed, so you can repeat same test again if you want. When your app crash, log with all necessary information (seed, number of events, logcat from device...) is saved to folder with your app's package name in current directory.

##Requirements
1. Linux or macOS with Android Debug Bridge installed
2. Device/emulator with Android 5.0+ and usb debugging enabled
3. All files from this repo in same folder

##How to
#####Run single test
1. Turn on the device, connect it to computer and open app for testing
2. Start `./monkey_madness` using terminal, you can specify optional arguments
  - argument1 - number of input events (touch, scroll, swipe...) that monkey will attempt to perform
  - argument2 - seed for generating random events (could be useful to repeat test which failed)
3. Script will lock app to full screen to prevent monkey escape
4. Monkey will furiously tap screen and try to crash your app
5. If monkey crashed your app, crash log is saved to folder with your app's package name in current directory

Example: `./monkey_madness 5000` - will start test with 5000 events, if app crash, log will be saved to folder with your app's package name in current directory.

#####Run multiple tests in a row
1. Turn on the device, connect it to computer and open app for testing
2. Start `./monkey_madness -l` or `./monkey_madness --loop` using terminal, you can specify optional arguments 
  - argument2 - number of tests to perform 
  - argument3 - number of input events (touch, scroll, swipe...) that will monkey attempt to perform in each test
  - seeds will be random
3. Your app will now be restarted
4. Script will lock app to full screen to prevent monkey escape
5. Monkey will furiously tap screen and try to crash your app
6. You see results of all tests, if monkey crashed your app, crash log is saved to folder with your app's package name in current directory

Example: `./monkey_madness -l 10 5000` - will start 10 consecutive tests each with 5000 events and random seed, if app crash, logs will be saved to folder with your app's package name in current directory.

#####Stop Monkey Madness
1. Don't disconnect USB! 
2. Press CTRL+C or close terminal or use `./kill_monkey`
3. Monkey is dead - log from interrupted test is saved to folder with your app's package name in current directory
 
##Warning
- Disable Messenger notifications when you use this tool! (If you want to prevent monkey from calling to random people and sending them messages.)
- Monkey won't stop its madness if you disconnect USB! If you do so, you need to reconnect it again and use `./kill_monkey`
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
