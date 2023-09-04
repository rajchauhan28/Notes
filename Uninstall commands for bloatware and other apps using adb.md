
Basic syntax - 
1) access  - `adb shell` to avoid repeating `adb shell` in all commands as repeated below `adb shell`
2) list installed packages `adb shell pm list packages` 
3) find package` adb shell pm list packages | grep '<OEM/Carrier/App Name>'`
4) uninstall `adb shell pm uninstall -k --user 0 NameOfPackage` 
5) or as a single command `adb shell pm uninstall --user 0 <package name>`


Some common Bloatware and apps -
 1) Smart Dock - `pm uninstall -k --user 0 cu.axel.smartdock`
 2) Samsung max - `pm uninstall -k --user 0 com.opera.max.oem`
 3) YouTube Vanced - `pm uninstall -k --user 0 com.vanced.android.youtube`
 4) YouTube - `pm uninstall -k --user 0 com.google.android.youtube`