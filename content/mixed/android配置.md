---
title: android配置
date: 2017-06-27 11:30:39
---

## app外build.gradle
```java
ext {
    minSdkVersion = 19
    targetSdkVersion = 28
    compileSdkVersion = 28
    supportLibraryVersion = "28.+"
}
```
## app内build.gradle
```java
android {
    compileSdkVersion rootProject.ext.compileSdkVersion
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
        debug {
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
    implementation "org.jetbrains.kotlin:kotlin-stdlib-jdk8:$kotlin_version"

    implementation 'androidx.appcompat:appcompat:1.0.0-rc01'
    implementation 'androidx.recyclerview:recyclerview:1.0.0-rc01'
    implementation 'androidx.cardview:cardview:1.0.0-rc01'
    implementation 'androidx.coordinatorlayout:coordinatorlayout:1.0.0-rc01'
    implementation 'androidx.constraintlayout:constraintlayout:2.0.0-alpha2'
//    implementation 'com.google.android.material:material:1.0.0-rc01'
//    implementation 'androidx.multidex:multidex:2.0.0'

    implementation 'androidx.core:core-ktx:1.0.0-rc01'

    implementation 'com.squareup.retrofit2:retrofit:2.4.0'
    implementation('com.squareup.retrofit2:converter-gson:2.4.0', {
        exclude group: 'com.google.code.gson'
    })
    implementation 'com.squareup.retrofit2:adapter-rxjava2:2.4.0'
    implementation 'com.squareup.okhttp3:logging-interceptor:3.11.0'
    implementation 'com.github.simonpercic:oklog3-java:2.3.0'

    implementation 'io.reactivex.rxjava2:rxjava:2.2.0'
    implementation 'io.reactivex.rxjava2:rxandroid:2.0.2'
    implementation 'com.trello.rxlifecycle2:rxlifecycle:2.2.2'
    implementation 'com.trello.rxlifecycle2:rxlifecycle-android:2.2.2'
    implementation 'com.trello.rxlifecycle2:rxlifecycle-components:2.2.2'
    implementation 'com.trello.rxlifecycle2:rxlifecycle-kotlin:2.2.2'
    implementation 'com.trello.rxlifecycle2:rxlifecycle-android-lifecycle-kotlin:2.2.2'
    implementation 'com.jakewharton.rxbinding2:rxbinding:2.1.1'
    implementation 'com.jakewharton.rxbinding2:rxbinding-support-v4:2.1.1'
    implementation 'com.jakewharton.rxbinding2:rxbinding-appcompat-v7:2.1.1'
    implementation 'com.jakewharton.rxbinding2:rxbinding-design:2.1.1'
    implementation 'com.tbruyelle.rxpermissions2:rxpermissions:0.9.5@aar'

    implementation 'com.google.code.gson:gson:2.8.5'
    implementation 'com.orhanobut:logger:2.2.0'
    implementation 'com.github.apl-devs:appintro:v4.2.3'
    implementation 'com.ashokvarma.android:bottom-navigation-bar:2.0.4'
    implementation 'com.youth.banner:banner:1.4.10'
    implementation 'de.hdodenhof:circleimageview:2.2.0'
    implementation 'com.github.CymChad:BaseRecyclerViewAdapterHelper:2.9.41'
    implementation 'com.scwang.smartrefresh:SmartRefreshLayout:1.1.0-alpha-14'
//    implementation 'com.flyco.tablayout:FlycoTabLayout_Lib:2.1.2@aar'

    implementation 'com.contrarywind:Android-PickerView:4.1.6'

    implementation 'com.blankj:utilcode:1.19.0'

    implementation 'com.github.bumptech.glide:glide:4.7.1'
    annotationProcessor 'com.github.bumptech.glide:compiler:4.7.1'

    implementation 'com.zhihu.android:matisse:0.5.2-beta3'

    implementation('com.github.qingmei2:rximagepicker:2.2.0-alpha', {
        exclude group: 'io.reactivex.rxjava2'
    })
    implementation 'com.github.qingmei2:rximagepicker_support_zhihu:2.2.0-alpha'

    implementation('com.blankj:rxbus:1.5', {
        exclude group: 'io.reactivex.rxjava2'
    })

    implementation 'com.github.chrisbanes:PhotoView:2.0.0'

    implementation 'com.sunfusheng:marqueeview:1.3.3'

    implementation 'org.apache.httpcomponents:httpcore:4.4.10'
    implementation 'com.daimajia.swipelayout:library:1.2.0@aar'
//    implementation 'com.github.barteksc:android-pdf-viewer:3.1.0-beta.1'

    implementation('com.lzy.net:okgo:3.0.4', {
        exclude group: 'com.squareup.okhttp3'
        exclude group: 'com.squareup.okio'
    })

    implementation "com.liulishuo.okdownload:okhttp:1.0.5"

//    implementation 'me.yokeyword:fragmentation:1.3.6'
}
```