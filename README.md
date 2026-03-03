
# 《小米手机系统优化对照表及说明》

小米手机性价比很高，做“备用机、移动热点、充电宝、红外遥控器、NFC钥匙、NFC交通卡、听歌神器、小型任务服务器、导航神器”都很适合，但是默认的手机系统很难说好用。

更新时间：2026-02-28，适配os1、os2、os3 ，可能仅限国行版。

教程地址： https://github.com/fyonecon/android-clean_hyperos 。

# 基础设置与安全说明：

1️⃣ 使用前备份好手机资料；

⚠️卡米时可清除手机全部数据重新开始（进入卡刷机模式）：

“关机（可长按 音量上+开关键 10s中关机），音量上+开关键 长按（大概10s），Logo出来立即只松开开关键，就可以进入清除模式。”；

2️⃣ 下面系统优化的操作旨在“提高系统隐私（如广告SDK、反诈、大数据统计）、删除系统广告、精简系统”，不会把手机当爷一样供着、不会注重省电和延长手机使用时间、不会帮助你Root破解手机、不会帮助你规避法律；

3️⃣ 可以在“澎湃1、澎湃2”中使用，操作前请备份手机数据到“云盘”或“手机以外的硬盘”，因为小米手机卡米变砖数据会彻底丢失；

4️⃣如下情况会卡米，不要操作⚠️：
```
com.android.htmlviewer HTML查看器不要卸载（重启卡米），可以停用；

com.miui.packageinstaller 应用包管理器不要卸载（重启卡米）；

com.xiaomi.metoknlp 网络位置不要卸载（切换系统明暗主题时会卡米）;

com.android.trace 程序追踪不要卸载（可能卡米）;
```

5️⃣ 尽量使用Win、Mac的ADB环境（下载Win或Mac的ADB工具：
https://developer.android.google.cn/tools/releases/platform-tools?hl=zh-cn 
），也可使用手机端ADB软件如“黑阈”；

6️⃣ 澎湃2比澎湃1好用，推荐澎湃2；澎湃3比澎湃2好用，推荐澎湃3。使用本教程从2升级到3重启时可能会卡米，建议先手动备份2文件系统到电脑里面，再升级到3；

7️⃣ 虚拟内存可以关闭或只设置为扩展4G，因为使用感知不强；

8️⃣ ⚠️关于权限“应用列表”、“设备ID、广告ID”，不管你是否用HyperOS权限管理还是Android权限管理，大陆App都可能获得的到，不管你是否手动设置拒绝、是否在Play商店里下载。（微信、JD、PDD不会获得）。

# 常用设置：

## 0. 断网，不插卡，不开Wi-Fi，不开蓝牙，设置-锁屏-自动锁屏时间设置为5min

## 1. 设置-应用-卸载所有预装应用（除了运动、录音、日历）

## 2. 设置负一屏，关闭广告，关闭卡片

## 3. 设置桌面，重点关闭上滑搜索、设置任务栏样式

## 4. 设置日历，关闭广告

## 5. 设置文件，关闭云盘

## 6. 设置相机，打开Live Photo，关闭位置

## 7. 设置-应用-其他应用（右上角）-关闭广告，关闭第三方应用统计

## 8. 设置-隐私-安全-关闭所有选项（各种安全检测、关闭广告、关闭网页链）

## 9. 设置-状态栏-控制中心-关闭智能设备，打开无字模式，打开网速显示，设置通知样式

## 10. 设置- Wi-Fi-网络加速-关闭网络切换

## 11. 设置-亮度与显示-刷新率设置为60Hz，字体默认大小+粗体

## 12. 设置-连续点击OS版本号，打开开发者模式-打开USB调试、动画设置为0.5倍、分辨率设置为327或339或340或350

## 13. 通讯录-关闭营业厅

## 14. 电话中拨号：

显示5G开关：
```
*#*#54638#*#*
```
显示VoLTE开关：
```
*#*#86583#*#*
```

## 15. 设置-更多设置-内存扩展-关闭

===自动重启手机===

## 16. 导入铃声、APK（可选）：

给手机导入铃声：
```
adb push ../android_backup/Files/铃声.zip /sdcard/Documents/
```

给手机导入APK：
```
adb push ../android_backup/Files/APK.zip /sdcard/Documents/
```

（到文件里面解压 铃声.zip 到 铃声目录 ，APK.zip到本级目录； 设置铃声<电话铃声、通知铃声、关闭锁屏声>，设置触感大小，

## 16.1. 下载基础APK安装包：

安装第三方提供的APK：
>
>LibCheck： https://www.downkuai.com/android/147630.html 
>
>DevCheck： https://www.ddooo.com/softdown/224201.htm 
>
>Edge浏览器： http://www.jxdown.com/soft/20238.html 
>
>Gboard输入法： http://www.jxdown.com/soft/42906.html
>
>类原生桌面： https://lawnchair.app/ （需在该App设置里手动关闭软件禁用）

也可以用本人提供的apk安装（在文件名中删掉.7z后缀就是.apk文件）：
> https://github.com/fyonecon/android-clean_hyperos/releases

免费VPN（300KB/s，下载有门槛）:
> https://play.google.com/store/apps/details?id=free.key.vpn&hl=zh_CN

）

顺便关闭“com.miui.packageinstaller #应用包管理器”到广告和安全检测功能（关闭系统优化时无此功能）

）

## 17. 用 DevCheck 设置，（用此软件的目的是调出原生安卓设置。可选。）：
```

“com.android.htmlviewer #HTML查看器”，关闭通讯录权限；

“com.miui.packageinstaller #应用包管理器”，关闭通讯录权限；

“com.android.providers.downloads #下载器”，关闭通讯录权限。

“com.xiaomi.metoknlp #网络位置”，关闭通讯录权限。

“com.xiaomi.account #小米账号”，关闭通讯录、电话权限。

“com.miui.home #系统桌面”，关闭通讯录、电话权限。

“com.xiaomi.bluetooth #小米蓝牙地图”，与系统蓝牙不是一回事，可能与生成蓝牙地图、物品找回有关。停用此app。

```

## 18. 设置-指纹与密码-锁屏密码、录入指纹

## 18.1 设置-应用-应用锁-将“系统更新”加入到应用锁

## 18.2 设置-隐私-隐藏应用-右上角开启密码验证

## 18.3 设置-更多设置-无障碍-（听觉-闪烁通知-选择黄色闪烁；视觉-显示大小-调到最大）

## 18.4 设置-更多设置-快捷手势-（按需设置快捷键）

## 18.5 设置-更多设置-账号与同步-打开“Google基础服务”。注意，os1、os2有效，os3中在小米应用商店中下载并安装“Google Play”即可完成开启Google服务。

## 18.6 设置-小米账号-关于小米账号-系统广告-关闭广告

## 18.7 设置-开发者模式-“App缓存优化”-打开。（这是小米官方替代“Google墓碑机制”国产App手段功能）

## 18.8 ⚠️设置-开发者模式-“系统优化”（os1、os2中可以直接看到，os3中连续点击“开发者模式-自动填充-重置为默认值”3次可以看到。）-关闭。
> 关闭时：
> 
> 1️⃣“app安装”变成android原生安装器；
> 
> 2️⃣字体设置可能失效或不能更改；
> 
> 3️⃣主题图标产生异常（小米自带app图标异常，反而别的应用可能是正常的，怀疑是小米故意恶心人）；
> 
> 4️⃣小米权限管理变成android原生权限管理（应用列表权限原生安卓中无此功能，而国内有，但是国内的这个应用权限功能只是个摆设和安慰剂功能）
> 
> 5️⃣应用自启设置不了，需要设置的话，可以恢复开启“系统优化”，设置好后再关闭“系统优化”；
>

（澎湃的纯净模式，近似原生安卓，此时内置的小米的安全追踪大部分关闭、系统主题部分失效<请提前设置好>、软件安装自由度火力全开、权限管理近似原生。）

## 19. 用ADB删除系统应用（⚠️⚠️⚠️“#”为暂时不要删除的应用，“#”越多，越不建议删⚠️⚠️⚠️）： 

获取当前安卓的用户标记，对多用户系统同样有用（如，0 、10 ）：
```
adb shell am get-current-user
```

### 必删App，广告与游戏：

```

adb shell pm uninstall --user 0 com.android.browser #小米浏览器

adb shell pm uninstall --user 0 com.miui.yellowpage #生活黄页(小米黄页)

adb shell pm uninstall --user 0 com.miui.hybrid #快应用服务框架(小米社区)

adb shell pm uninstall --user 0 com.miui.analytics #小米广告分析

adb shell pm uninstall --user 0 com.miui.systemAdSolution #小米系统广告解决方案

adb shell pm uninstall --user 0 com.miui.guardprovider #反诈

adb shell pm uninstall --user 0 com.miui.bugreport #用户bug反馈

adb shell pm uninstall --user 0 com.miui.securityadd #游戏加速

adb shell pm uninstall --user 0 com.xiaomi.gamecenter.sdk.service #小米游戏中心服务

adb shell pm uninstall --user 0 com.xiaomi.gamecenter #小米游戏中心（os1中可用）

adb shell pm uninstall --user 0 com.xiaomi.macro #自动连招

adb shell pm uninstall --user 0 com.miui.misightservice #系统质量检测（os3中有）

adb shell pm uninstall --user 0 com.xiaomi.security.onetrack #用户数据收集与统计

```

### 可删App，性能与墓碑机制：

> 小米电池与性能:
> 
> 1.关闭锁屏自动杀应用后台功能：设置--电池--更多电池功能--锁屏后清理内存--选「从不」。这个功能是“安全中心”负责。；
> 
> 2.每个应用按需设置「后台联网」；
> 
> 3.每个应用按需设置「后台运行」（这是安卓原生权限设置）；
> 
> 4.有些小米系统自带应用不可设置。）


> 联发科机器“快霸（Duraspeed）”App的使用：
> 
> 默认关闭情况：消息、后台很及时，但是对内存和电池消耗可能过快。
> 
>手动打开+app里设置白名单：特别省内存，会杀死一些垃圾进程，但是消息会延迟，FCM消息即使加了白名单也会延迟，对微信无任何影响。
> 
> 如何打开快霸app：LibCheck--搜“duraspeed”--点击duraspeed的logo--点击“设置”--“打开”。


```

adb shell pm uninstall --user 0 com.xiaomi.joyose #小米性能云控

adb shell pm uninstall --user 0 com.xiaomi.mtb #鲁班MTB（系统性能调节）

adb shell pm uninstall --user 0 com.mobiletools.systemhelper #智能系统优化（含有百度地图SDK）

adb shell pm uninstall --user 0 com.miui.daemon #系统质量服务（匿名数据收集）

###adb shell pm uninstall --user 0 com.miui.powerkeeper #电量和性能（智能杀后台应用，后台保活，后台保活设置）

```

### 可删App，小米服务：

```

adb shell pm uninstall --user 0 com.miui.miservice #服务反馈

adb shell pm uninstall --user 0 com.milink.service #互联互通服务

adb shell pm uninstall --user 0 com.xiaomi.mi_connect_service #小米互联互通服务

adb shell pm uninstall --user 0 com.miui.carlink #CarWith

adb shell pm uninstall --user 0 com.xiaomi.ab #小米售后支持

adb shell pm uninstall --user 0 com.miui.phrase #常用语（无卵用）

adb shell pm uninstall --user 0 com.miui.contentcatcher #应用扩展服务（也与广告有关）

#adb shell pm uninstall --user 0 com.xiaomi.payment #米币支付（含有银联SDK）

adb shell pm uninstall --user 0 com.unionpay.tsmservice.mi #银联统计

adb shell pm uninstall --user 0 com.wapi.wapicertmanager #WAPI证书

adb shell pm uninstall --user 0 com.miui.thirdappassistant #第三方应用分析（主要针对32位应用）

adb shell pm uninstall --user 0 com.android.adservices.api #谷歌安卓系统广告隐私保护

adb shell pm uninstall --user 0 com.miui.mishare.connectivity #小米分享（废物应用）

#adb shell pm uninstall --user 0 com.miui.nextpay #卡包网页组件（小米钱包、NFC管理等）

adb shell pm uninstall --user 0 com.android.healthconnect.controller #健康数据共享

adb shell pm uninstall --user 0 com.google.android.configupdater #（可能与小米系统权限恢复有关）

#adb shell pm uninstall --user 0 com.miui.touchassistant #悬浮球

#adb shell pm uninstall --user 0 com.miui.contentextension #传送门（识屏）

#adb shell pm uninstall --user 0 com.miui.accessibility #小米闻声

#adb shell pm uninstall --user 0 com.miui.mediaviewer #媒体查看器(MXPlayer代替)

adb shell pm uninstall --user 0 com.miui.greenguard #家人守护、系统未成年模式

adb shell pm uninstall --user 0 com.xiaomi.bluetooth #小米额外的蓝牙服务（不是安卓蓝牙）

#adb shell pm uninstall --user 0 com.xiaomi.digitalkey #小米数字车钥匙

```

### 可删App，增值服务：

```

###adb shell pm uninstall --user 0 com.lbe.security.miui #MIUI权限管理（可用安卓自带权限管理代替。默认国内权限全开，原生安卓权限需要手动设置。）

######adb shell pm uninstall --user 0 com.miui.securitycenter #安全服务（无界面，电池管理、应用列表、隐藏应用、应用联网、手机改名、应用锁、应用杀毒、地震预警，请用“LibCheck https://www.downkuai.com/android/147630.html ”软件代替管理应用列表）

############adb shell pm uninstall --user 0 com.xiaomi.xmsf #⚠️小米服务框架（微信消息、APP后台消息推送（可与FCM共存）、MiPush、设备统计相关、用户大数据分析等）

############adb shell pm uninstall --user 0 com.miui.securitycore #⚠️系统功能服务组件（应用双开、手机分身、系统多开、边缘触控）

############adb shell pm uninstall --user 0 com.xiaomi.misettings #⚠️小米设置（不是Android设置。设置铃声、设置应用使用时间限制、设置刷新率、机车运动模式、大屏模式）

############adb shell pm uninstall --user 0 com.android.settings.intelligence #⚠️搜索原生Android设置（比如，新增系统语言与地区<非hyperos已经固定的语言>、调取应用列表 等）

#adb shell pm uninstall --user 0 com.miui.core #MIUI SDK（自动安装系统软件、SDK等）

#adb shell pm uninstall --user 0 com.miui.core.internal.services #（绑定在Android系统中，实际用途未找到未明确）

#adb shell pm uninstall --user 0 com.sohu.inputmethod.sogou.xiaomi #搜狗输入法（微信输入法、GBoard输入法代替）

adb shell pm uninstall --user 0 com.miui.securitycenter.securitycenter_phone_overlay.config.overlay #(不知道)

###adb shell pm uninstall --user 0 com.android.mms #短信（谷歌短信App代替）

######adb shell pm uninstall --user 0 com.android.contacts #电话、通讯录、营业厅（谷歌电话App、联系人App代替。os1、os2中可删，os3中请保留。）

#adb shell pm uninstall --user 0 com.xiaomi.market #小米应用商店，请在此下载安装Google Play（别的商店代替，推荐vivo H5应用商店 （ https://h5.appstore.vivo.com.cn ）、Google Play）

###adb shell pm uninstall --user 0 com.google.android.webview #Webview(可能含有网址访问认证，Google Play里面下别的版本的webview代替)

###adb shell pm uninstall --user 0 com.android.thememanager #系统主题(设置)（主题、图标、壁纸设置好了以后再删除此App）

#adb shell pm uninstall --user 0 com.android.providers.downloads #下载器（下载主题、下载系统、自动下载和安装App。如果需要更新系统，ADB恢复下载器软件+重启手机。）

adb shell pm uninstall --user 0 com.android.quicksearchbox #桌面搜索

#######adb shell pm uninstall --user 0 com.miui.personalassistant #桌面负一屏（小部件、安卓小部件入口、负一平智能助理）

############adb shell pm uninstall --user 0 com.miui.home #⚠️小米桌面（可以用第三方桌面替代，比如GooglePlay里面的“迷你桌面”。但是 最近任务、导航栏 消失）

```

### 可删App， 小爱同学（人工智障，按需卸载）：

```

############adb shell pm uninstall --user 0 com.miui.voicetrigger #语音唤醒小爱

############adb shell pm uninstall --user 0 com.miui.voiceassist #小爱同学、超级小爱

adb shell pm uninstall --user 0 com.xiaomi.aicr #MiAI引擎、澎湃AI引擎

adb shell pm uninstall --user 0 com.xiaomi.aireco #小爱建议

adb shell pm uninstall --user 0 com.xiaomi.aiasst.vision #小爱翻译

adb shell pm uninstall --user 0 com.xiaomi.scanner #小爱视觉（还需要在小爱视觉设置-关于-关闭“上传图片图片识别优化”）

adb shell pm uninstall --user 0 com.xiaomi.aiasst.service #小爱通话

```

### 可删App，小米账号与云服务（谨慎卸载）

```

adb shell pm uninstall --user 0 com.miui.cloudbackup #小米云备份

adb shell pm uninstall --user 0 com.miui.cloudservice #小米云服务（查找设备<仅能中国大陆ID>、同步“相册、蓝牙、笔记、录音”，可以用GooglePhoto、GoogleKeep、OneDrive代替） #adb shell pm uninstall --user 0 com.xiaomi.micloud.sdk #小米云服务SDK

adb shell pm uninstall --user 0 com.miui.micloudsync #小米云同步（仅同步“联系人、通话、短信、安全服务、Wi-Fi”，可以用Google服务代替。）

############adb shell pm uninstall --user 0 com.xiaomi.account #小米账号（绑定任意国家ID：防止手机刷机，启用小爱同学，启用小米运动，退出小米账号后可以删除）

############adb shell pm uninstall --user 0 com.android.updater #小米系统更新（需要与“com.android.providers.downloads”下载器搭配才能更新系统）

```

===手动重启手机===

## 20. 手机联网

## 21. 在小米应用商店下载“Google Play”。
安装完成后卸载掉小米应用商店（关闭广告相关开关以后还会推送广告，必须卸载）：
```
adb shell pm uninstall --user 0 com.xiaomi.market
```

## 22. 更改密码填充服务。
设置-更多设置-语言与输入法-密码和帐号-首选服务-选择小米账号或者Google或Edge浏览器或Auth认证App（这是密码自动填充服务）

===（手动重启手机）===

## 22. 连上VPN Wi-Fi，在GooglePlay下载：
Google电话、Google短信、Google Photo、微信、Yahoo天气、windy、Onedrive、Firefox、三星浏览器、Google Keep、Spotify等

## 23. 登录微信（需要下载小程序扩展）；Firefox添加ad扩展（打开Firefox的“添加桌面快捷方式”权限，如果【设置-开发者模式-“系统优化”】已经关闭，这无此快捷方式权限）。

## 24. Firefox或三星浏览器添加vivo H5应用商店（ https://h5.appstore.vivo.com.cn ）到桌面快捷方式。

## 25. 最后，如果玩机玩累了，请转到其他家的手机。

# 恢复已删除App、系统数据清除等：

1️⃣ 恢复已删除的预装应用举例：

adb shell cmd package install-existing （应用包名）

```

adb shell cmd package install-existing com.xiaomi.market #小米应用商店

adb shell cmd package install-existing com.android.providers.downloads #下载管理器

adb shell cmd package install-existing com.android.updater #小米系统更新

adb shell cmd package install-existing com.lbe.security.miui #MIUI权限管理（可用安卓自带权限管理代替）

adb shell cmd package install-existing com.miui.securitycenter #安全服务（无界面、应电池、应用列表、隐藏应用、应用联网、手机名+Wi-Fi名+蓝牙名更改校验）

adb shell cmd package install-existing com.android.thememanager #系统主题(设置)

adb shell cmd package install-existing com.android.mms #短信

adb shell cmd package install-existing com.android.contacts #电话和通讯录

adb shell cmd package install-existing com.miui.personalassistant #桌面负一屏(小部件、智能助理)

adb shell cmd package install-existing com.miui.securitycore #系统功能服务组件（应用双开、手机分身、边缘触控）

adb shell cmd package install-existing com.miui.cloudservice #小米云服务

adb shell cmd package install-existing com.xiaomi.account #小米账号

adb shell cmd package install-existing com.miui.micloudsync #小米云同步

adb shell cmd package install-existing com.xiaomi.xmsf #小米服务（微信消息、Mipush）

adb shell cmd package install-existing com.miui.powerkeeper #电量和性能（智能杀后台应用，后台保活相关）

adb shell cmd package install-existing com.android.camera #小米相机

adb shell cmd package install-existing com.miui.core #（系统SDK API）

adb shell cmd package install-existing com.miui.home #小米桌面

```

禁用和恢复禁用的命令：
```
禁用：
adb shell pm disable-user [应用包名]

恢复禁用：
adb shell pm enable [应用包名]

```

禁止后台联网的命令：
```
禁用：
adb shell cmd netpolicy add restrict-background [应用包名]

验证：
adb shell cmd netpolicy list restrict-background

恢复：
adb shell cmd netpolicy remove restrict-background [应用包名]

```

2️⃣ 给手机导入导出文件（示例）：

将手机系统备份文件夹导入电脑中：
adb pull /sdcard/MIUI/backup/AllBackup ../android_backup/

将电脑文件夹导入手机系统恢复文件夹中：
adb push ../android_backup/AllBackup /sdcard/MIUI/backup/

给手机导入铃声：
adb push ../android_backup/Files/铃声.zip /sdcard/Documents/

给手机导入APK：
adb push ../android_backup/Files/APK.zip /sdcard/Documents/

给手机导入卡刷包：
adb push ../android_backup/OS/RedmiNote14Pro-CN-malachite-ota_full-OS2.0.10.0.VOOCNXM-user-15.0-13718ddde6.zip /sdcard/Documents/ 

============================

# 一次性运行代码

adb push ../android_backup/ /sdcard/Download/ ;

```

adb shell pm uninstall --user 10 com.android.browser;

adb shell pm uninstall --user 10 com.miui.yellowpage;

adb shell pm uninstall --user 10 com.miui.hybrid;

adb shell pm uninstall --user 10 com.miui.analytics;

adb shell pm uninstall --user 10 com.miui.systemAdSolution;

adb shell pm uninstall --user 10 com.miui.guardprovider;

adb shell pm uninstall --user 10 com.miui.bugreport;

adb shell pm uninstall --user 10 com.miui.securityadd;

adb shell pm uninstall --user 10 com.xiaomi.gamecenter.sdk.service;

adb shell pm uninstall --user 10 com.xiaomi.macro;

adb shell pm uninstall --user 10 com.miui.misightservice;

adb shell pm uninstall --user 10 com.xiaomi.security.onetrack;

adb shell pm uninstall --user 10 com.xiaomi.joyose;

adb shell pm uninstall --user 10 com.xiaomi.mtb;

adb shell pm uninstall --user 10 com.mobiletools.systemhelper;

adb shell pm uninstall --user 10 com.miui.daemon;

adb shell pm uninstall --user 10 com.miui.miservice;

adb shell pm uninstall --user 10 com.milink.service;

adb shell pm uninstall --user 10 com.xiaomi.mi_connect_service;

adb shell pm uninstall --user 10 com.miui.carlink;

adb shell pm uninstall --user 10 com.xiaomi.ab;

adb shell pm uninstall --user 10 com.miui.phrase;

adb shell pm uninstall --user 10 com.miui.contentcatcher;

adb shell pm uninstall --user 10 com.xiaomi.payment;

adb shell pm uninstall --user 10 com.unionpay.tsmservice.mi;

adb shell pm uninstall --user 10 com.wapi.wapicertmanager;

adb shell pm uninstall --user 10 com.miui.thirdappassistant;

adb shell pm uninstall --user 10 com.android.adservices.api;

adb shell pm uninstall --user 10 com.miui.mishare.connectivity;

adb shell pm uninstall --user 10 com.miui.nextpay;

adb shell pm uninstall --user 10 com.android.healthconnect.controller;

adb shell pm uninstall --user 10 com.google.android.configupdater;

adb shell pm uninstall --user 10 com.miui.touchassistant;

adb shell pm uninstall --user 10 com.miui.contentextension;

adb shell pm uninstall --user 10 com.miui.accessibility;

adb shell pm uninstall --user 10 com.miui.mediaviewer;

adb shell pm uninstall --user 10 com.miui.greenguard;

adb shell pm uninstall --user 10 com.xiaomi.bluetooth;

adb shell pm uninstall --user 10 com.miui.core;

adb shell pm uninstall --user 10 com.miui.core.internal.services;

adb shell pm uninstall --user 10 com.miui.securitycenter.securitycenter_phone_overlay.config.overlay;

adb shell pm uninstall --user 10 com.android.quicksearchbox;

adb shell pm uninstall --user 10 com.xiaomi.digitalkey;

adb shell pm uninstall --user 10 com.miui.voicetrigger

adb shell pm uninstall --user 10 com.xiaomi.aicr;

adb shell pm uninstall --user 10 com.xiaomi.aireco;

adb shell pm uninstall --user 10 com.xiaomi.aiasst.vision;

adb shell pm uninstall --user 10 com.xiaomi.scanner;

adb shell pm uninstall --user 10 com.xiaomi.aiasst.service;

adb shell pm uninstall --user 10 com.miui.cloudbackup;

adb shell pm uninstall --user 10 com.miui.cloudservice;

adb shell pm uninstall --user 10 com.xiaomi.micloud.sdk;

adb shell pm uninstall --user 10 com.miui.micloudsync;

adb shell pm uninstall --user 10 com.lbe.security.miui;

adb shell pm uninstall --user 10 com.miui.securitycenter;

adb shell pm uninstall --user 10 com.sohu.inputmethod.sogou.xiaomi;

adb shell pm uninstall --user 10 com.xiaomi.market;

```


========================
