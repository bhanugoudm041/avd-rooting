# avd-rooting
rooting avds NOTE: view it raw mode


Rooting android studio emulator;
Note: git & adb(added to path) should be installed before you run this commands

In a Terminal, execute these commands:
git clone https://github.com/newbit1/rootAVD.git
cd rootAVD
adb devices


WINDOWS(at the end it does not shuts off automatically shut it down manually)

In the Command Prompt, execute this command:
rootAVD.bat
Execute the correct one for your emulator, which is probably API 30 or 29 x86_64 as shown below:
rootAVD.bat system-images\android-29(replace it with android version your using)\google_apis\x86_64\ramdisk.img
lot of messages scroll by, and your emulator shuts off.




MAC or Linux(at the end it does not shuts off automatically shut it down manually)

In the Command Prompt, execute this command:
rootAVD.sh
You see a long list of commands for many Android versions. Execute the correct one for your emulator, which is probably API 30, x86_64 as shown below:
rootAVD.sh system-images\android-29(replace it with android version your using)\google_apis\x86_64\ramdisk.img
A lot of messages scroll by, and your emulator shuts off.


Cold Booting your Emulator
In Android Studio, in Device Manager, on the line showing your device, at the right side, click the down-arrow, and click "Cold Boot Now", as shown below.

then run
adb shell
su
a prompt will be shown in android quickly click grant thats it root is installed magisk also installed on the emulator



INSTALLING XPOSED FRAMEWORK IN ANDROID STUDIO EMULATOR(download all below repositories to windows or linux and simply drag and drop them to android emulator they copied to android)

Download or clone riru from this repository
https://github.com/RikkaApps/Riru/releases

open magisk and go to modules select option select module from storage choose riru zip it will be installed and reboot.


Download or clone edxoposed from this repository
stable version
https://magisk.me/xposed-framework-magisk-module/

alpha version
https://github.com/ElderDrivers/EdXposed/releases

open magisk and go to modules select option select module from storage choose xposed zip it will be installed and reboot.(sometimes it will not be installed and redirect us to riru page and throws an error riru is not installed to fix it download old version of riru try to repeat the installation of xposed)

Now go to this below repository and download xposed app 
https://github.com/ElderDrivers/EdXposedManager/releases

reboot the device
now xposed framework is properly installed open xposed maganer app and install required moduels


# someother methods super SU
second method

adb root
adb shell getenforce

output
-->
Enforcing

adb shell "setenforce 0"

adb shell getenforce
output
-->
Permissive


adb shell "mount -t tmpfs -o size=15M tmpfs /system/xbin"  
after mounting the storage checking mount point you will get read and write permission
adb shell "cat /proc/mounts | grep /system/xbin"
output
-->
tmpfs /system/xbin tmpfs rw,seclabel,relatime,size=15360k 0 0

cd c:\temp\x64   (push all the files from the zip after unzipping it(here its x64bit i uploaded x64bit files))
adb push .\ "/system/xbin/"
-->
.\: 5 files pushed, 0 skipped. 85.6 MB/s (872152 bytes in 0.010s)


adb shell "ls -l /system/xbin"
-->
libsupol.so
su
suinit
sukernel
supolicy


cd c:\temp
adb install SuperSU-v2.82-SR5.apk
-->
Performing Streamed Install
Success

adb shell "nohup /system/xbin/su 0 su --daemon &"

adb shell "ps -ef | grep daemonsu"
-->
..
..daemonsu:mount:master
..daemonsu:master
..

open super su app and cancel update (NOTE: dont update)

https://anthony-f-tannous.medium.com/android-10-emulation-of-magisk-supersu-on-an-aosp-avd-de93ed080fad
