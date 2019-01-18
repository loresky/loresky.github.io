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


******
```
dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])
    implementation "org.jetbrains.kotlin:kotlin-stdlib-jdk8:$kotlin_version"
    implementation 'com.android.support.constraint:constraint-layout:1.1.3'
    //noinspection GradleCompatible
    implementation 'com.android.support:appcompat-v7:28.0.0'
    //noinspection GradleCompatible
    implementation 'com.android.support:cardview-v7:28.0.0'
    //noinspection GradleCompatible
    implementation 'com.android.support:design:28.0.0'


    implementation 'com.google.code.gson:gson:2.8.5'
    implementation 'com.orhanobut:logger:2.2.0'
    implementation 'com.youth.banner:banner:1.4.10'
    implementation 'de.hdodenhof:circleimageview:3.0.0'
    implementation 'com.zhihu.android:matisse:0.5.2-beta3'
    implementation 'com.github.chrisbanes:PhotoView:2.0.0'
    implementation 'com.github.CymChad:BaseRecyclerViewAdapterHelper:2.9.46'
    implementation 'com.scwang.smartrefresh:SmartRefreshLayout:1.1.0-alpha-19'
//    implementation 'com.flyco.tablayout:FlycoTabLayout_Lib:2.1.2@aar'
    //引导
//    implementation 'com.github.apl-devs:appintro:v4.2.3'
    //选择器
    implementation 'com.contrarywind:Android-PickerView:4.1.7'
    //侧滑删除
    implementation 'com.daimajia.swipelayout:library:1.2.0@aar'
//    implementation 'com.daimajia.numberprogressbar:library:1.4@aar'
    //跑马灯
//    implementation 'com.sunfusheng:marqueeview:1.3.3'
    //bottom-navigation
//    implementation 'com.github.ittianyu:BottomNavigationViewEx:2.0.2'
//    implementation 'com.ashokvarma.android:bottom-navigation-bar:2.1.0'
    //鲁班图片压缩
    implementation 'top.zibin:Luban:1.1.8'
    //工具类库
    implementation 'com.blankj:utilcode:1.22.10'

    implementation 'com.github.bumptech.glide:glide:4.8.0'
    annotationProcessor 'com.github.bumptech.glide:compiler:4.8.0'

    implementation 'com.squareup.retrofit2:retrofit:2.5.0'
    implementation('com.squareup.retrofit2:converter-gson:2.5.0', {
        exclude group: 'com.google.code.gson'
    })

    implementation 'com.squareup.retrofit2:adapter-rxjava2:2.5.0'
    implementation 'com.squareup.okhttp3:logging-interceptor:3.12.1'
    implementation 'com.github.simonpercic:oklog3-java:2.3.0'

    implementation 'io.reactivex.rxjava2:rxjava:2.2.5'
    implementation 'io.reactivex.rxjava2:rxandroid:2.1.0'
//    implementation 'com.trello.rxlifecycle3:rxlifecycle:3.0.0'
//    implementation 'com.trello.rxlifecycle3:rxlifecycle-android:3.0.0'
//    implementation 'com.trello.rxlifecycle3:rxlifecycle-components:3.0.0'
//    implementation 'com.trello.rxlifecycle3:rxlifecycle-components-preference:3.0.0'
//    implementation 'com.trello.rxlifecycle3:rxlifecycle-android-lifecycle:3.0.0'
//    implementation 'com.trello.rxlifecycle3:rxlifecycle-kotlin:3.0.0'
//    implementation 'com.trello.rxlifecycle3:rxlifecycle-android-lifecycle-kotlin:3.0.0'
//    implementation 'com.jakewharton.rxbinding3:rxbinding:3.0.0-alpha2'
//    implementation 'com.jakewharton.rxbinding2:rxbinding-support-v4:2.1.1'
//    implementation 'com.jakewharton.rxbinding2:rxbinding-appcompat-v7:2.1.1'
//    implementation 'com.jakewharton.rxbinding2:rxbinding-design:2.1.1'
    implementation 'com.tbruyelle.rxpermissions2:rxpermissions:0.9.5@aar'

    implementation('com.blankj:rxbus:1.5', {
        exclude group: 'io.reactivex.rxjava2'
    })

    implementation('com.lzy.net:okgo:3.0.4', {
        exclude group: 'com.squareup.okhttp3'
        exclude group: 'com.squareup.okio'
    })

    //版本更新 https://github.com/AlexLiuSheng/CheckVersionLib
    implementation 'com.allenliu.versionchecklib:library:2.1.8'


    //webview使用post参数要用到
//    implementation 'org.apache.httpcomponents:httpcore:4.4.10'

//    implementation 'com.just.agentweb:agentweb:4.0.2'
//    implementation 'com.just.agentweb:download:4.0.2'
//    implementation 'com.just.agentweb:filechooser:4.0.2'

    //pdf
//    implementation 'com.github.barteksc:android-pdf-viewer:3.1.0-beta.1'


    implementation 'me.yokeyword:fragmentation:1.3.6'

    //微信
    implementation 'com.tencent.mm.opensdk:wechat-sdk-android-with-mta:+'

    //圆角，边框，Gradient背景渐变，控件State各个状态UI样式
    implementation 'com.ruffian.library:RWidgetHelper:1.0.7'


//    implementation 'com.jakewharton:butterknife:10.0.0'
//    annotationProcessor 'com.jakewharton:butterknife-compiler:10.0.0'

    debugImplementation 'com.squareup.leakcanary:leakcanary-android:1.6.3'
    releaseImplementation 'com.squareup.leakcanary:leakcanary-android-no-op:1.6.3'

    testImplementation 'junit:junit:4.12'
    androidTestImplementation 'com.android.support.test:runner:1.0.2'
    androidTestImplementation 'com.android.support.test.espresso:espresso-core:3.0.2'
}
```
### proguard-rules.pro
```
#BaseRecyclerViewAdapterHelper
-keep class com.chad.library.adapter.** {
*;
}
-keep public class * extends com.chad.library.adapter.base.BaseQuickAdapter
-keep public class * extends com.chad.library.adapter.base.BaseViewHolder
-keepclassmembers public class * extends com.chad.library.adapter.base.BaseViewHolder {
           <init>(android.view.View);
}

#Glide
-keep public class * implements com.bumptech.glide.module.GlideModule
-keep public class * extends com.bumptech.glide.module.AppGlideModule
-keep public enum com.bumptech.glide.load.ImageHeaderParser$** {
  **[] $VALUES;
  public *;
}

# for DexGuard only
-keepresourcexmlelements manifest/application/meta-data@value=GlideModule

#Matisse
-dontwarn com.bumptech.glide.**

#tencent
-keep class com.tencent.mm.opensdk.** {
    *;
}

-keep class com.tencent.wxop.** {
    *;
}

-keep class com.tencent.mm.sdk.** {
    *;
}

#CheckVersionLib
-keepattributes Annotation
-keepclassmembers class * {
   @org.greenrobot.eventbus.Subscribe;
}
-keep enum org.greenrobot.eventbus.ThreadMode {
   *;
}
-keepclassmembers class * extends org.greenrobot.eventbus.util.ThrowableFailureEvent {
   (java.lang.Throwable);
}
 -keep class com.allenliu.versionchecklib.** {
   *;
}

#AgentWeb
-keep class com.just.agentweb.** {
    *;
}
-dontwarn com.just.agentweb.**
```
