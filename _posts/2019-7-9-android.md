
---
date: 2018-9-9 09:50:47+00:00
layout: post
title: 'android key'
categories: 技术 
tags:  androd
---

1.什么是签名，有什么用
Android APP都需要我们用一个证书对应用进行数字签名，不然的话是无法安装到Android手机上的，平时我们调试运行时到手机上时，是AS会自动用默认的密钥和证书来进行签名；但是我们实际发布编译时，则不会自动签名，这个时候我们就需要进行手动签名了！ 为我们的APK签名有以下好处：

1.应用程序升级：如果你希望用户无缝升级到新的版本，那么你必须用同一个证书进行签名。这是由于只有以同一个证书签名，系统才会允许安装升级的应用程序。如果你采用了不同的证书，那么系统会要求你的应用程序采用不同的包名称，在这种情况下相当于安装了一个全新的应用程序。如果想升级应用程序，签名证书要相同，包名称要相同！
2.应用程序模块化： Android系统可以允许同一个证书签名的多个应用程序在一个进程里运行，系统实际把他们作为一个单个的应用程序，此时就可以把我们的应用程序以模块的方式进行部署，而用户可以独立的升级其中的一个模块。
3.代码或者数据共享： Android提供了基于签名的权限机制，那么一个应用程序就可以为另一个以相同证书签名的应用程序公开自己的功能。以同一个证书对多个应用程序进行签名，利用基于签名的权限检查，你就可以在应用程序间以安全的方式共享代码和数据了。 不同的应用程序之间，想共享数据，或者共享代码，那么要让他们运行在同一个进程中，而且要让他们用相同的证书签名。 ————上述内容摘自:android 为什么需要签名

2.Android Studio如何打包签名

2.1 如何生产key
Build -> Generate Signed APK...
注意： keystore path必须是绝对路基


2.2 apply in gradle file


```
android {
    signingConfigs {
        signingkey {
            keyAlias 'key0'
            keyPassword 'abcd1234'
            storeFile file('../test.jks')
            storePassword 'abcd1234'
        }
    }


    buildTypes {
        debug {

        }
        release {
            signingConfig signingConfigs.signingkey
        }
    }
```









