---
title: android配置
date: 2017-06-27 11:30:39
tags: android
---

## app外build.gradle
```java
ext {
    minSdkVersion = 19
    targetSdkVersion = 23
    compileSdkVersion = 25
    buildToolsVersion = "25.0.2"
    supportLibraryVersion = "25.+"
}
```
## app内build.gradle
```java
android {
    compileSdkVersion rootProject.ext.compileSdkVersion
    buildToolsVersion rootProject.ext.buildToolsVersion
	
    defaultConfig {
        minSdkVersion rootProject.ext.minSdkVersion
        targetSdkVersion rootProject.ext.targetSdkVersion     
    }
	
	signingConfigs {
        release {
            storeFile file("loresky.jks")
            storePassword "123456"
            keyAlias "loreskykey"
            keyPassword "123456"
        }
    }
	buildTypes {
        release {
//            signingConfig signingConfigs.release
            // 是否进行dex优化
            zipAlignEnabled false
            // 支持删除一些没有用的资源
            shrinkResources false
            // 是否进行混淆
            minifyEnabled false
            // 混淆文件位置
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
        debug {
//            signingConfig signingConfigs.release
            minifyEnabled false
            shrinkResources false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
    // 移除lint检查的error
    lintOptions {
        abortOnError false
    }
    dataBinding {
        enabled = true
    }
}
repositories {
    flatDir {
        //就是你放aar的目录地址
        dirs 'libs'
    }
}

dependencies {
    compile "com.android.support:appcompat-v7:$supportLibraryVersion"
    androidTestCompile('com.android.support.test.espresso:espresso-core:2.2.2', {
        exclude group: 'com.android.support', module: 'support-annotations'
        exclude group: 'com.google.code.findbugs'
    })
}
```