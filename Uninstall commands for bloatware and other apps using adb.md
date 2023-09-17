
Basic syntax - 
1) access  - `adb shell` to avoid repeating `adb shell` in all commands as repeated below `adb shell`

2) list installed packages `adb shell pm list packages` 

3) find package` adb shell pm list packages | grep '<OEM/Carrier/App Name>'`

4) uninstall `adb shell pm uninstall -k --user 0 NameOfPackage` 

5) or as a single command `adb shell pm uninstall --user 0 <package name>`


Some common Bloatware and apps -
 1) Smart Dock - `pm uninstall -k --user 0 cu.axel.smartdock` also uninstall another cu.axel.smartdock app from app list in your phone
 2) Samsung max - `pm uninstall -k --user 0 com.opera.max.oem`

 3) YouTube Vanced - `pm uninstall -k --user 0 com.vanced.android.youtube`

 4) YouTube - `pm uninstall -k --user 0 com.google.android.youtube`

 5) My Galaxy  - `com.mygalaxy`

 6) Netflix - `Com.netflix.mediaclient`

 7) Google duo - `Com.google.android.apps.tachyon`

 9) LinkedIn - `com.linkedin.android`

 10) OneDrive - 

 11) Google App - `com.google.android.googlequicksearchbox`

 12) YouTube - `com.google.android.youtube`

 13) Chrome - `com.android.chrome` && `com.sec.android.app.chromecustomizations`

 14) Google Market Feedback Agent - `com.google.android.feedback`

 15) Google Photos - `com.google.android.apps.photos`

 16) Google Print Service Recommendation Service - `com.google.android.printservice.recommendation`

 17) Google sync contacts - `com.google.android.syncadapters.contacts`

 18) Google sync calendar - `com.google.android.syncadapters.calendar`

 19) Google Music - `com.google.android.music`

 20) Google Maps - `com.google.android.apps.maps`

 21) Google Drive - `com.google.android.apps.docs`

 22) Google Duo - `com.google.android.apps.tachyon`

 23) Google Play Movies & TV - `com.google.android.videos`

 24) Google Gmail - `com.google.android.gm`

 25) X Google Enrollment - `com.android.hotwordenrollment.xgoogle`

 26) OK Google Enrollment - `com.android.hotwordenrollment.okgoogle`

 27) Device Health Services - `com.google.android.apps.turbo`

 28) Android Setup Wizard - `com.google.android.setupwizard`

 29) Android Setup Restore - `com.google.android.apps.restore`

 30) Google One Time Init - `com.google.android.onetimeinitializer`

 31) Samsung Smart Switch - `com.sec.android.easyMover` && `com.sec.android.easyMover.Agent` && `com.samsung.android.smartswitchassistant`

 32) Samsung Finder - `com.samsung.android.app.galaxyfinder`

 33) Samsung What’s New - `com.samsung.android.app.social`

 34) Kids Home Installer - `com.samsung.android.kidsinstaller`

 35) Kids Mode friends - `com.samsung.android.app.camera.sticker.facearavatar.preload`

 36) Led Cover - `com.sec.android.cover.ledcover` && `com.samsung.android.app.ledbackcover`

 37) Samsung Media and devices feature - `com.samsung.android.mdx.quickboard`

 38) Bixby =`com.samsung.android.app.settings.bixby` 
					```com.samsung.systemui.bixby2`
					com.samsung.android.bixby.service`
					com.samsung.android.bixby.agent`
					com.samsung.android.bixby.wakeup`
					com.samsung.android.bixby.agent.dummy```

 39) Bixby Vision - `com.samsung.android.visionintelligence
					`com.samsung.android.bixbyvision.framework`

40) Samsung Daily - `com.samsung.android.app.spage`

42) Samsung Email - `com.samsung.android.email.provider`

43) Bixby Routines - `com.samsung.android.app.routines`

44) Facebook - ```com.facebook.appmanager
					com.facebook.services
					com.facebook.katana
					com.facebook.system```

45) LinkedIn -  `com.linkedin.android`

46) Microsoft Onedrive - `com.microsoft.skydrive`

47) Samsung SmartThings - `com.samsung.android.oneconnect`

48) Samsung Global Goals - `com.samsung.sree`

49) Samsung Tips - `com.samsung.android.app.tips`

50) Samsung Members - `com.samsung.android.voc`

51) Google Text-to-speech - `com.google.android.tts`
``
52) Google Partner Setup - `com.google.android.partnersetup`

53) Android Auto - `com.google.android.projection.gearhead`

53) CarmodeStub - `com.samsung.android.drivelink.stub`

54) Samsung MirrorLink - `com.samsung.android.app.mirrorlink`

55) Samsung Weather - `com.sec.android.daemonapp`

56) Android Easter Egg - `com.android.egg`

57) Samsung EasyOneHand - `com.sec.android.easyonehand`

58) Galaxy Essentials Widget - `com.sec.android.widgetapp.samsungapps`

59) Samsung Galaxy Friends - `com.samsung.android.mateagent`

60) Samsung Pay Framework
`com.samsung.android.spayfw`

61) Hiya, Call Blocker, Fraud Detection & Caller ID
`com.hiya.star`

62) Samsung Smart Call
`com.samsung.android.smartcallprovider`

63) Samsung Pass - `com.samsung.android.authfw`

64) Samsung Pass Provider - `com.samsung.android.samsungpass`

65) Samsung Pass Autofill - `com.samsung.android.samsungpassautofill`

66) Samsung AR Emoji - `com.samsung.android.aremoji`

67) Samsung Live Message - `com.samsung.android.service.livedrawing`

68) Samsung My Emoji Stickers - `com.sec.android.mimage.avatarstickers`

69) Print Spooler - `com.android.printspooler`

70) Default Print Service - `com.android.bips`

71) Samsung Digital Wellbeing & Parental Controls - `com.samsung.android.forest`

72) Samsung Configuration Message - `com.wsomacp`

73) Samsung Game Launcher - `com.samsung.android.game.gamehome
com.samsung.android.game.gametools
com.samsung.android.game.gos`

74) Samsung Reminder - `com.samsung.android.app.reminder`

75) Samsung EdgeScreen - `com.samsung.android.app.cocktailbarservice`
76) Samsung quicktools (edgescreen) - `com.sec.android.app.quicktool`
77) Samsung Internet Panel (Edgescreen) - `com.samsung.android.app.sbrowseredge`
78) Samsung Tasks (Edgescreen) - `com.samsung.android.app.taskedge`
79) Samsung Apps (Edgescreen) - `com.samsung.android.app.appsedge`
80) Samsung Clipboard (Edgescreen) - `com.samsung.android.app.clipboardedge`
81) Samsung People (Edgescreen) - `com.samsung.android.service.peoplestripe`

82) Samsung Customization Service - `com.samsung.android.rubin.app`

83) Samsung Dictionary - `com.diotek.sec.lookup.dictionary`

84) Favorite Contacts - `com.sec.android.widgetapp.easymodecontactswidget`

85) Samsung Secure Wi-Fi - `com.samsung.android.fast`

86) Samsung Partner Bookmarks - `com.android.providers.partnerbookmarks`

87) Samsung SmartThings - `com.samsung.android.easysetup`

88) Samsung SmartThings (Bluetooth/wifi tracking beacons in shops?) - `com.samsung.android.beaconmanager`

89) Wi-Fi Tips - `com.samsung.android.net.wifi.wifiguider`

90) Samsung Upday - `de.axelspringer.yana.zeropage`

91) Samsung OM Customize (Vodafone app?) - `com.sec.android.omc`

92) Samsung Cloud - `com.samsung.android.scloud`

93) Samsung AR Doodle - `com.samsung.android.ardrawing`