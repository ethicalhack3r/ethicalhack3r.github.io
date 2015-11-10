---
layout: post
status: publish
published: false
title: Mobile Security Certificate Pinning
excerpt: "Certificate Pinning is an extra layer of security that is used by applications to ensure that the certificate provided by the remote server is the one which is expected.
\r\n\r\n
By including the remote server’s x509 certificate or public key within the application, it is possible to compare the locally stored certificate or key with the one provided by the remote server.
\r\n\r\n
If you have been unable to intercept (Man-in-the-Middle) the application’s HTTPS traffic, after taking the necessary steps, this is probably due to the application using Certificate Pinning."
---

# Mobile Security Certificate Pinning

Certificate Pinning is an extra layer of security that is used by applications to ensure that the certificate provided by the remote server is the one which is expected.

By including the remote server’s x509 certificate or public key within the application, it is possible to compare the locally stored certificate or key with the one provided by the remote server.

If you have been unable to intercept (Man-in-the-Middle) the application’s HTTPS traffic, after taking the necessary steps, this is probably due to the application using Certificate Pinning.

## Bypassing Certificate Pinning

Certificate Pinning is a client-side security measure that can be bypassed by manipulating the application or its environment.

Applications can be disassembled to remove or manipulate the certificate pinning logic. It may also be possible to switch the certificate embedded within the application with another.

Some tools exist for different mobile platforms which can automatically disable certificate pinning. These tools may not necessarily be kept up to date and you may need to try the manual approaches discussed above.

### iOS Applications

Both of the following tools need jailbroken devices as they manipulate the application or device during runtime to disable Certificate Pinning.

- iOS SSL Kill Switch patches low-level SSL functions within the Secure Transport API - https://github.com/iSECPartners/ios-ssl-kill-switch

- iOS TrustMe disables SecTrustEvaluate - https://github.com/intrepidusgroup/trustme 

### Android Applications

Both of the following tools need rooted devices as they manipulate the application or device during runtime to disable Certificate Pinning.

- Android-SSL-TrustKiller hooks various runtime methods to bypass certificate pinning - https://github.com/iSECPartners/Android-SSL-TrustKiller 

- android-ssl-bypass uses a JDWP debugger using the JDI APIs - https://github.com/iSECPartners/android-ssl-bypass

## Real World Certificate Pinning Bypass Example

To further demonstrate how Certificate Pinning can be bypassed, we will walk through the necessary steps to bypass Certificate Pinning implemented in the official Facebook Android application.

These exact steps may not work for you if you are following them step-by-step against the official Facebook Android application as Facebook may have changed the way they implement their certificate pinning from the time when these steps were first written. However, they should still be useful to gain an understanding of how applications can be manipulated to bypass certificate pinning.

This was reported to Facebook via their Bug Bounty program incase they considered it a security issue which could be protected against. According to Facebook, using a modified APK to bypass certificate pinning is not eligible for their bug bounty program.

The first step is to download the Facebook APK from the Play Store. Once downloaded we will disassemble the application, modify the source code, reassemble the application, sign the application and then finally, install it onto a device.

### Disassembling the APK

The [apktool](https://github.com/iBotPeaches/Apktool) tool was used to disassemble the APK with the following command:

    $ apktool d com.facebook.katana.apk -o com.facebook.katana_disassembled

### Modify the Certificate Pinning logic

Once the APK has been disassembled we will need to locate where within the smali source code the certificate pinning checks are done. Searching the smali code for keywords such as “X509TrustManager”, “cert”, “pinning”, etc, should point you in the right direction.

In this case a search for “X509TrustManager” returned a result within the ‘smali/com/facebook/acra/util/TrustEveryoneTrustManager.smali’ file. This file contains methods named “checkClientTrusted”, “checkServerTrusted” and “getAcceptedIssuers”.

The “return-void” opcode was added to the first line of each of these methods. The “return-void” statement is a Dalvik opcode to return ‘void’ or null. For more Dalvik opcodes refer to http://pallergabor.uw.hu/androidblog/dalvik_opcodes.html 

### Reassembling the APK

Once the changes are made to the methods the APK will need to be reassembled. To do this the following apktool command was run:

    $ apktool b com.facebook.katana_disassembled/ -o app_modified.apk

This should create a reassembled APK named ‘app_modified.apk’ with the changes we made.

### Signing the APK

Before the modified APK can be installed onto a device it needs to be cryptographically signed. To sign the app_modified.apk APK file the following steps should be taken:

1.Generate the private key.

    $ keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000

2.Sign the APK using the generated private key.

    $ jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore app_modified.apk

The modified APK should now be signed for 10,000 days and ready to be installed onto the Android device. To do this, ensure the device has USB debugging enabled then attach the device to the computer’s USB port and run:

    $ adb install app_modified.apk

After installing the modified APK it is possible to intercept (Man-in-the-Middle) the HTTPS communications.

## Conclusions

This content was originally written for the up and coming OWASP Mobile Application Security Testing Guide. However, I have decided to share it here so that others can benefit from my research and write up before the OWASP guide is officially released. It should also help improve the final version as it should generate more feedback.

If you have any feedback please leave a comment - https://docs.google.com/document/d/16sMdEmDk3cGR1qAZwFFCPu_M2t3t4g6sYydTzRu7274/edit

This post demonstrates the extra security which Certificate Pinning can offer in mobile applications, as well as how trivially it can be bypassed in some circumstances.
