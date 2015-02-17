---
layout: post
title: "PhoneGap学习-1.android环境搭建"
image:
feature: abstract-10.jpg
tags: [PhoneGap]
comments: true
share: true
---


![PhoneGap title](http://pic.yupoo.com/edyang/Erj1hGCU/medish.jpg)

## 资源

* [官方网站](http://25.io/smaller/)
* [Phonegap中国](http://www.phonegapcn.com/)
* [官网教程](http://docs.phonegap.com/en/edge/guide_platforms_index.md.html)
* more

------

## 让我们开始吧


### 1. 配置要求： 
	Eclipse 3.4+ or IntelliJ Idea 13+

### 2. 安装SDK+PhoneGap

![eclipse](http://www.phonegapcn.com/start/zh/1.3/index_files/eclipse.png) 下载安装 [Ecipse Classic](http://www.eclipse.org/downloads/)  

![android sdk](http://www.phonegapcn.com/start/zh/1.3/index_files/android.png) 下载安装 [Android Sdk](http://developer.android.com/sdk/index.html)  

![android sdk](http://www.phonegapcn.com/start/zh/1.3/index_files/android.png) 下载安装 [ADT Plugin](http://developer.android.com/sdk/eclipse-adt.html#installing)  

![PhoneGap](http://www.phonegapcn.com/start/zh/1.3/index_files/phonegap.png) 下载安装 [PhoneGap](http://phonegap.com/download)  解压后将会使用Android目录

### 3. 设置新项目

* 打开 Eclipse,在文件菜单下面点击 新建 > Android Project
* 在项目的根目录, 创建两个目录:
	* /libs
	* /assets/www
* 从刚才下载的PhoneGap中复制phonegap.js到/assets/www目录
* 从刚才下载的PhoneGap中复制phonegap.jar到/lib目录
* 从刚才下载的PhoneGap中复制xml到/res目录
* 对Eclipse 的src文件夹中的主java文件进行少量调整，如下：

<!-- lang:java -->
	package com.j2sf.pg.eva;
	import android.os.Bundle;
	import org.apache.cordova.DroidGap;
	public class EVA extends DroidGap {//继承自DroidGap
   		 
    	@Override
    	public void onCreate(Bundle savedInstanceState) {
        	super.onCreate(savedInstanceState);
        	super.loadUrl("file:///android_asset/www/index.html");//修改setContentView();
    	}
	}
<!-- lang:java -->

## 4. 编辑AndroidManifest.xml

* 权限设置xml文件改动如下：
<!-- lang:xml -->
    <?xml version="1.0" encoding="utf-8"?>
    <manifest xmlns:android="http://schemas.android.com/apk/res/android"
              package="com.j2sf.pg.eva"
              android:versionCode="1"
              android:versionName="1.0">
    
        <supports-screens
                android:largeScreens="true"
                android:normalScreens="true"
                android:smallScreens="true"
                android:resizeable="true"
                android:anyDensity="true"
                /> <!--添加-->
    
        <!--phoneGap需要的权限-->
        <uses-permission android:name="android.permission.CAMERA" />
        <uses-permission android:name="android.permission.VIBRATE" />
        <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
        <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
        <uses-permission android:name="android.permission.ACCESS_LOCATION_EXTRA_COMMANDS" />
        <uses-permission android:name="android.permission.READ_PHONE_STATE" />
        <uses-permission android:name="android.permission.INTERNET" />
        <uses-permission android:name="android.permission.RECEIVE_SMS" />
        <uses-permission android:name="android.permission.RECORD_AUDIO" />
        <uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS" />
        <uses-permission android:name="android.permission.READ_CONTACTS" />
        <uses-permission android:name="android.permission.WRITE_CONTACTS" />
        <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
        <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
        <uses-permission android:name="android.permission.GET_ACCOUNTS" />
        <!--phoneGap需要的权限-->
    
        <uses-sdk android:minSdkVersion="19"/>
        <application android:label="@string/app_name" android:icon="@drawable/ic_launcher">
            <activity android:name="EVA"
                      android:label="@string/app_name"
                      android:configChanges="orientation|keyboardHidden">
                <intent-filter>
                    <action android:name="android.intent.action.MAIN"/>
                    <category android:name="android.intent.category.LAUNCHER"/>
                </intent-filter>
            </activity>
        </application>
    </manifest>

<!-- lang:xml -->

##5. Hello word 程序编写
在`/assets/www` 目录中新建index.html文件，并粘贴如下代码：
<!-- lang:xml -->
    <!DOCTYPE HTML>
    <html>
    <head>
        <title>PhoneGap</title>
        <script type="text/javascript" charset="utf-8" src="cordova.js"></script>
    </head>
    <body>
    <h1>Hello World</h1>
    </body>
    </html>
<!-- lang:xml -->

##6. OK 运行吧！ 
 

![](http://j2sf.com/favicon.png) www.j2sf.com

