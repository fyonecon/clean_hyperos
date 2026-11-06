
# <a id="no-0"></a>《小米手机系统优化对照表及注解》

更新时间：2026-10-20（细节补充版），适配HyperOS1、HyperOS2、HyperOS3 ，可能仅限国行版。PS，基于Android17的HyperOS4只能用disable和enable，因此此教程可能无法适应于OS4。

原创教程地址： https://github.com/fyonecon/clean_hyperos 。

### 目标：

- 本教程实操先优化“已开启小米系统优化”情况下的手机系统，期间或逐步对比并说明“关闭小米手机系统优化”情况下的手机系统功能变化。

- 本教程旨在“彻底清除系统广告”和“彻底断绝与反诈有关的系统App（含SDK）”，清爽你的手机系统。适合将小米手机作为备用机的情况。

- 本教程含有大量注释说明，需要花费大量时间阅读与理解。

- 【万能方法】如果你不想看本教程，不知道你是哪个系统版本，不会知道哪家安卓手机，也不想删除或冻结系统软件，可以用快速路径优化你的系统（拦截任何广告、阻断隐私安全），安装 BlockADs（开源+免费）https://blockads.pwhs.app 。

### 大纲：

- [一、安全说明](#no-1)
- [二、深度设置手机](#no-2)
- [三、用ADB删除系统应用](#no-3)
- [四、小米系统扩展用法](#no-4)
- [五、恢复已删除App](#no-5)
- [End 吐槽](#no-end)

------


# <a id="no-1"></a>一、安全说明：

### 1. 使用前备份好手机资料：

救砖办法：
- ⚠️卡米时可清除手机全部数据重新开始（进入卡刷机模式）：

- “关机（可长按 音量上+开关键 10s中关机），音量上+开关键 长按（大概10s），Logo出来立即只松开开关键，就可以进入清除模式。”；

### 2. 下面系统优化的操作旨在“提高系统隐私（如广告SDK、反诈、大数据统计）、删除系统广告、精简系统、更接近原生Android”，不会注重省电和延长手机使用时间（隔夜消耗4%左右的电，不联网也会消耗这么多电）、不会帮助你Root破解手机；

### 3. 可以在“澎湃1、澎湃2、澎湃3”中使用，操作前请备份手机数据到“云盘”或“手机以外的硬盘”，因为小米手机卡米变砖数据会彻底丢失。可能不适用于澎湃4，这需要你自己甄别和尝试；

### 4. ⚠️如下情况会卡米，不要操作⚠️：
```
com.android.htmlviewer HTML查看器不要卸载（重启卡米），可以停用；

com.miui.packageinstaller 应用包管理器不要卸载（重启卡米）；

com.xiaomi.metoknlp 网络位置不要卸载（切换系统明暗主题时会卡米）;

com.xiaomi.location.fused 小米融合位置不要卸载（切换系统明暗主题时会卡米）;

com.miui.miwallpaper 小米壁纸（屏幕直接黑屏，任何东西都看不到）;

```

### 5. 搭建Win、Mac的ADB环境：
下载Win或Mac的ADB工具：
> https://developer.android.google.cn/tools/releases/platform-tools?hl=zh-cn 

如果浏览器下载不了就用迅雷( https://www.xunlei.com )下。

也可使用手机端ADB软件如“黑阈”。

⚠️两种开发者模式说明：
  - 初级开发者模式：在开发者模式的“USB调试、无线调试”这2个按钮。能删除大多数系统应用。【删除不了最核心系统应用但也不能避免卡米】；
  - 高级级开发者模式：在开发者模式的“USB调试、USB调试（安全模式）、无线调试”这3个按钮。其中打开“USB调试（安全模式）”时要求登录小米账号com.xiaomi.account + 有安全服务com.miui.securitycenter软件，此开关打开后，可删除一些系统保护的软件如小米finddevice。【可删除最核心系统应用但也不能避免卡米】；

### 6. 澎湃2比澎湃1好用，推荐澎湃2；澎湃3比澎湃2好用，推荐澎湃3。使用本教程从2升级到3重启时可能会卡米，建议先手动备份2文件系统到电脑里面，再升级到3；

### 7. 虚拟内存可以关闭或只设置为扩展4G，因为使用感知不强；开了多用户系统时请开启虚拟内存到8G。这有利于多系统软件切换后保活；基于Android16的HyperOS3无内置16KB页面固件，只能运行4KB页面。

### 8. ⚠️关于权限“应用列表”、“设备ID、广告ID”，不管你是否用HyperOS权限管理还是Android权限管理，大陆App都可能获得的到，不管你是否手动设置拒绝、是否在Play商店里下载。（微信、JD、PDD不会暗地里获得应用列表）。

### 9. 常用手机设置，根据你的需要设置即可：

- 「可选」：断网，不插卡，不开Wi-Fi，不开蓝牙，设置-锁屏-自动锁屏时间设置为5min

- 设置-应用-卸载所有预装应用（除了运动、录音、日历）

- 设置负一屏，关闭广告，关闭卡片

- 设置桌面，重点关闭上滑搜索、设置任务栏样式

- 设置日历，关闭广告

- 设置文件，关闭云盘

- 设置相机，打开Live Photo，关闭位置

- 设置-应用-其他应用（右上角）-关闭广告，关闭第三方应用统计

- 设置-隐私-安全-关闭所有选项（各种安全检测、关闭广告、关闭网页链）

- 设置-状态栏-控制中心-关闭智能设备，打开无字模式，打开网速显示，设置通知样式

- 设置- Wi-Fi-网络加速-关闭网络切换

- 设置-亮度与显示-刷新率设置为60Hz，字体默认大小+粗体

- 设置-连续点击OS版本号，打开开发者模式-打开USB调试、动画设置为0.5倍、分辨率设置为327或339或340或350

- 通讯录-关闭营业厅

- 电话中拨号：

    显示 5G 开关（手动切换到4G网络模式下用，一直默认5G太费电了）：
    ```
    *#*#54638#*#*
    ```
    显示 4G VoLTE 开关：
    ```
    *#*#86583#*#*
    ```

- 「可选」设置-更多设置-内存扩展-关闭，然后根据提示重启手机


------


# <a id="no-2"></a>二、深度设置手机：

### 1. 继续设置手机：
- 「可选」：断网，不插卡，不开Wi-Fi，不开蓝牙

- 设置-指纹与密码-锁屏密码、录入指纹

- 设置-应用-应用锁-将“系统更新”加入到应用锁

- 设置-隐私-隐藏应用-右上角开启密码验证

- 设置-更多设置-无障碍-（听觉-闪烁通知-选择黄色闪烁；视觉-显示大小-调到最大）

- 设置-更多设置-快捷手势-（按需设置快捷键）

- 设置-更多设置-账号与同步-打开“Google基础服务”。注意，os1、os2有效，os3中在小米应用商店中下载并安装“Google Play”即可完成开启Google服务。

- 设置-小米账号-关于小米账号-系统广告-关闭广告

- 设置-开发者模式-“App缓存优化”-打开。（这是小米官方替代“Google墓碑机制”国产App手段功能）

- ⚠️设置-开发者模式-“系统优化”（os1、os2中可以直接看到，os3中连续点击“开发者模式-自动填充-重置为默认值”3次可以看到。）-关闭。

  关闭“系统优化”后会出现：
    - “app安装”变成android原生安装器 < 后经过使用发现，这功能还不一定成立，因为澎湃系统OS中含有某种未证实的多系统用户策略，比如第一个多用户的功能会被限制。。 >；
    - 字体设置可能失效或不能更改 < 后经过软件分析发现，人为Bug。。 >；
    - 主题图标产生异常（仅限小米桌面App中，小米自带app图标异常，反而别的应用可能是正常的，怀疑是小米故意恶心人 < 后经过软件分析发现，小米桌面App软件中的众多功能没有解耦。。 > ）；
    - 小米权限管理变成android原生权限管理（应用列表权限原生安卓中无此功能，而国内有 < 后经过系统和软件分析发现，这是社会主义特色。。 > ）；
    - 应用自启设置不了，需要设置的话，可以恢复开启“小米系统优化”，设置好后再关闭“小米系统优化” < 后经过系统结构分析发现，这是“一SYS两制”。。 > 。

  注意：澎湃的纯净模式，近似原生安卓，此时内置的小米的安全追踪大部分关闭、系统主题部分失效<请提前设置好>、软件安装自由度火力全开、权限管理近似原生。

### 2. 「可选」用ADB导入 铃声、APK 实例：

给手机导入铃声：
```
adb push ../android_backup/Files/铃声.zip /sdcard/Documents/
```

给手机导入APK：
```
adb push ../android_backup/Files/APK.zip /sdcard/Documents/
```

到文件里面解压 铃声.zip 到 铃声目录 ，APK.zip到本级目录； 设置铃声<电话铃声、通知铃声、关闭锁屏声>，设置触感大小。

### 3. 下载第三方基础APK安装包：

```
防止手机无法使用：
- 安装一个浏览器，比如Edge、三星浏览器、Firefox；
- 安装一个输入法，比如GBoard、微信输入法。
```

安装第三方提供的APK：

>
>LibCheck： https://www.downkuai.com/android/147630.html 
>
>DevCheck： https://www.ddooo.com/softdown/224201.htm 
>
>Edge浏览器： http://www.jxdown.com/soft/20238.html 
>
>Firefox浏览器： https://www.ddooo.com/softdown/189287.htm 
>
>三星浏览器： https://www.ddooo.com/softdown/149726.htm
>
>Gboard输入法： http://www.jxdown.com/soft/42906.html
>
>类原生桌面lawnchair： https://lawnchair.app/ （需在该App设置里手动关闭软件禁用才能设置默认桌面）
> 
> 如下，使用第三方软件+ADB来代替小米系统的对第三方桌面下的导航手势限制：
> - 安装第三方手势导航软件 Ogesture（ https://github.com/tanujnotes/Ogesture ），打开该软件无障碍（先在桌面长按Ogesture的图标进入到“关于软件”-底部有三个点到按钮，打开“允许软件限制”，顺便设置电池为无限制，再打开手机设置-更多设置-无障碍-已下载应用-开启无障碍）；
> - 打开Ogesture软件，开启手势导航 后 即可使用手势导航了；
> - 隐藏三大金刚键（无办法，重启手机后会失效，无论adb或shizuku）。
> 
>系统隐藏设置查找（Activity Launcher）： https://www.malavida.com/en/soft/activity-launcher/android/
>
> 谷歌相机： https://gcamapk.io/zh-CN/download-gcam-apk/
> 

顺便关闭“com.miui.packageinstaller #应用包管理器”到广告和安全检测功能（关闭小米系统优化时无此功能）。

### 4. 更改密码填充服务。
设置-更多设置-语言与输入法-密码和帐号-首选服务-选择小米账号或者Google或Edge或Firefox浏览器或Auth认证App（这是密码自动填充服务）

### 5. 用 DevCheck 调出系统应用的隐藏设置（可选。）：
```

“com.android.htmlviewer #HTML查看器”，关闭通讯录权限；

“com.miui.packageinstaller #应用包管理器”，关闭通讯录权限；

“com.android.providers.downloads #下载器”，关闭通讯录权限。

“com.xiaomi.metoknlp #网络位置”，关闭通讯录权限。

“com.xiaomi.account #小米账号”，关闭通讯录、电话权限。

“com.miui.home #系统桌面”，关闭通讯录、电话权限。

“com.xiaomi.bluetooth #小米蓝牙地图”，与系统蓝牙不是一回事，可能与生成蓝牙地图、物品找回有关。停用此app。

```

### 6. 在小米应用商店下载并安装“Google Play”


------


# <a id="no-3"></a>三、用ADB删除系统应用（⚠️⚠️⚠️“#”为暂时不要删除的应用，“#”越多，越不建议删⚠️⚠️⚠️）： 

### 1. 获取当前安卓的用户标记，对多用户系统同样有用（如，0 、10、11 ）：

```
adb shell am get-current-user
```

### 2. 必删App，广告与游戏：

```

adb shell pm uninstall --user 0 com.android.browser #小米浏览器（含有网址审查）

adb shell pm uninstall --user 0 com.miui.yellowpage #生活黄页(小米黄页)

adb shell pm uninstall --user 0 com.miui.hybrid #快应用服务框架（野蛮广告）

adb shell pm uninstall --user 0 com.miui.analytics #小米广告分析

adb shell pm uninstall --user 0 com.miui.systemAdSolution #小米系统广告解决方案

adb shell pm uninstall --user 0 com.miui.guardprovider #上报至反诈中心

adb shell pm uninstall --user 0 com.miui.bugreport #用户bug反馈

adb shell pm uninstall --user 0 com.miui.securityadd #游戏加速等

adb shell pm uninstall --user 0 com.xiaomi.gamecenter.sdk.service #小米游戏中心服务

adb shell pm uninstall --user 0 com.xiaomi.gamecenter #小米游戏中心（os1中可用）

adb shell pm uninstall --user 0 com.xiaomi.macro #自动连招

adb shell pm uninstall --user 0 com.miui.misightservice #系统质量检测（os3中有）

adb shell pm uninstall --user 0 com.xiaomi.security.onetrack #用户数据收集与统计

adb shell pm uninstall --user 0 com.mobiletools.systemhelper #注册机主手机号、位置、硬件等用于信息收集（含有百度地图SDK）

```

### 3. 可删App，性能与墓碑机制：

> 小米电池与性能:
> 
> - 关闭锁屏自动杀应用后台功能：设置--电池--更多电池功能--锁屏后清理内存--选「从不」。这个功能是“安全中心”负责。；
> 
> - 每个应用按需设置「后台联网」；
> 
> - 每个应用按需设置「后台运行」（这是安卓原生权限设置）；
> 
> - 有些小米系统自带应用不可设置。


> 联发科机器“快霸（Duraspeed）”App的使用：
> 
> - 默认关闭情况：消息、后台很及时，但是对内存和电池消耗可能过快。
> 
> - 手动打开+app里设置白名单：特别省内存，会杀死一些垃圾进程，但是消息会延迟，FCM消息即使加了白名单也会延迟，对微信无任何影响。
> 
> - 如何打开快霸app（有效否待验证）：LibCheck--搜“duraspeed”--点击duraspeed的logo--点击“设置”--“打开”。


```

adb shell pm uninstall --user 0 com.android.traceur #系统进程追踪

adb shell pm uninstall --user 0 com.xiaomi.joyose #小米性能云控

adb shell pm uninstall --user 0 com.xiaomi.mtb #鲁班MTB（系统性能调节）

adb shell pm uninstall --user 0 com.miui.daemon #系统质量服务（匿名数据收集）

adb shell pm uninstall --user 0 com.miui.powerkeeper #电量和性能（智能杀后台应用，后台保活，后台保活设置。与设置里面的“电池”还不一样，设置里面的“电池”由“com.miui.securitycenter #安全服务”管理。关闭“系统优化”后，非常建议删除。）

```

### 4. 可删App，小米服务：

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

#############adb shell pm uninstall --user 0 com.tencent.soter.soterserver #微信指纹支付（删了不影响微信支付）

adb shell pm uninstall --user 0 com.wapi.wapicertmanager #WAPI证书

adb shell pm uninstall --user 0 com.miui.thirdappassistant #第三方应用分析（主要针对32位应用）

adb shell pm uninstall --user 0 com.android.adservices.api #谷歌安卓系统广告隐私保护

adb shell pm uninstall --user 0 com.miui.mishare.connectivity #小米分享（废物应用）

adb shell pm uninstall --user 0 com.android.healthconnect.controller #健康数据共享

adb shell pm uninstall --user 0 com.google.android.configupdater #（可能与小米系统权限恢复有关）

#adb shell pm uninstall --user 0 com.miui.touchassistant #悬浮球

#adb shell pm uninstall --user 0 com.miui.contentextension #传送门（识屏）

#adb shell pm uninstall --user 0 com.miui.accessibility #小米闻声

#adb shell pm uninstall --user 0 com.miui.mediaviewer #媒体查看器(MXPlayer代替)

adb shell pm uninstall --user 0 com.miui.greenguard #家人守护、系统未成年模式

adb shell pm uninstall --user 0 com.xiaomi.bluetooth #小米额外的蓝牙服务（不是安卓蓝牙。可能与附近手机设备、附近穿戴设备有关。）

#adb shell pm uninstall --user 0 com.xiaomi.digitalkey #小米数字车钥匙

#adb shell pm uninstall --user 0 com.xiaomi.continuity.sdkapp #继续服务（协同播放、投屏？）

#adb shell pm uninstall --user 0 com.miui.autoui.ext #？

#adb shell pm uninstall --user 0 com.mi.AutoTest #售后测试

#adb shell pm uninstall --user 0 com.miui.tsmclient #小米智能卡

#adb shell pm uninstall --user 0 com.miui.wmsvc #似乎与快应用的信息服务有关（有人说与NFC充值也有关）

#adb shell pm uninstall --user 0 com.miui.nextpay #卡包网页组件（小米钱包、NFC管理等）

#############adb shell pm uninstall --user 0 com.xiaomi.camera 相机

#############adb shell pm uninstall --user 0 com.xiaomi.cameramind 相机图片后台合成任务

#############adb shell pm uninstall --user 0 com.xiaomi.finddevice 小米查找设备（需要3项开发者权限开启）

```

### 5. 可删App，增值服务：

```

#############adb shell pm uninstall --user 0 com.lbe.security.miui #MIUI权限管理（可用安卓自带权限管理代替。默认国内权限全开，原生安卓权限需要手动设置。）

#############adb shell pm uninstall --user 0 com.miui.securitycenter #安全服务（无界面，电池管理、应用列表、隐藏应用、应用联网、手机改名、OAID<删除securitycenter后App获取OAID将为空>、应用锁、应用杀毒、地震预警、NFC充值，请用“LibCheck https://www.downkuai.com/android/147630.html ”软件代替管理应用列表。如果“关闭小米手机系统优化”，强烈建议删除此App，以获得接近原声安卓的体验。此app与系统及的“全屏红色倒计时弹窗”提醒有关，卸载后提醒变成无全屏弹窗倒计时的小蓝色弹窗。此外，app与取证有关（未证实）。分身空间（不是多用户空间）删除后重启手机会自动恢复。）

#############adb shell pm uninstall --user 0 com.xiaomi.xmsf #⚠️小米服务框架（微信消息、APP后台消息推送（可与Google FCM共存）、MiPush、设备统计相关、用户大数据分析等）

#############adb shell pm uninstall --user 0 com.xiaomi.xmsfkeeper #⚠️小米服务框架Keeper

############adb shell pm uninstall --user 0 com.miui.securitycore #⚠️系统功能服务组件（应用双开、手机分身、系统多开、边缘触控）

#adb shell pm uninstall --user 0 com.miui.core #MIUI SDK（自动安装系统软件、SDK等）

#adb shell pm uninstall --user 0 com.miui.core.internal.services #（绑定在Android系统中，实际用途未找到未明确）

adb shell pm uninstall --user 0 com.miui.securitycenter.securitycenter_phone_overlay.config.overlay #(不知道)

#############adb shell pm uninstall --user 0 com.android.mms #短信（谷歌短信App代替）

#############adb shell pm uninstall --user 0 com.android.contacts #电话、通讯录、营业厅（谷歌电话App、联系人App代替。os1、os2中可删，os3中请保留。）

#############adb shell pm uninstall --user 0 com.google.android.webview #Webview(可能含有网址访问认证，Google Play里面下别的版本的webview代替)

#############adb shell pm uninstall --user 0 com.android.thememanager #系统主题(设置)（主题、图标、壁纸设置好了以后再删除此App，或者使用第三方相册设置壁纸。）

#############adb shell pm uninstall --user 0 com.android.updater #小米系统更新（需要与“com.android.providers.downloads”下载器搭配才能更新系统）

adb shell pm uninstall --user 0 com.android.quicksearchbox #桌面搜索

#######adb shell pm uninstall --user 0 com.miui.personalassistant #桌面负一屏（小米小部件、安卓小部件、负一平智能助理）

##########################adb shell pm uninstall --user 0 com.miui.home #⚠️小米桌面（可以用第三方桌面<如 https://lawnchair.app/ >替代。但是“最近任务、导航栏”消失。别删！）

```

### 6. 可删App， 小爱同学（人工智障，按需卸载）：

```

#############adb shell pm uninstall --user 0 com.miui.voicetrigger #语音唤醒小爱

#############adb shell pm uninstall --user 0 com.miui.voiceassist #小爱同学、超级小爱

adb shell pm uninstall --user 0 com.xiaomi.aicr #MiAI引擎、澎湃AI引擎

adb shell pm uninstall --user 0 com.xiaomi.aireco #小爱建议

adb shell pm uninstall --user 0 com.xiaomi.aiasst.vision #小爱翻译

adb shell pm uninstall --user 0 com.xiaomi.scanner #小爱视觉（还需要在小爱视觉设置-关于-关闭“上传图片图片识别优化”）

adb shell pm uninstall --user 0 com.xiaomi.aiasst.service #小爱通话

```

### 7. 可删App，小米账号与云服务（谨慎卸载）

```

adb shell pm uninstall --user 0 com.miui.cloudbackup #小米云备份

adb shell pm uninstall --user 0 com.miui.cloudservice #小米云服务（查找设备<仅能中国大陆ID>、同步“相册、蓝牙、笔记、录音”，此app可能与小米账号联动上报用户串联信息。可以用GooglePhoto、GoogleKeep、OneDrive代替）
 
#adb shell pm uninstall --user 0 com.xiaomi.micloud.sdk #小米云服务SDK

adb shell pm uninstall --user 0 com.miui.micloudsync #小米云同步（仅同步“联系人、通话、短信、安全服务、Wi-Fi”，可以用Google服务代替。）

adb shell pm uninstall --user 0 com.miui.backup #备份（只能备份有备案的App的资料，不能备份国外或者未备案App资料）

#############adb shell pm uninstall --user 0 com.xiaomi.account #小米账号（绑定任意国家ID：防止手机刷机，启用小爱同学，启用小米运动，退出小米账号后可以删除）

#############adb shell pm uninstall --user 0 com.sohu.inputmethod.sogou.xiaomi #搜狗输入法（微信输入法、GBoard输入法代替）

#############adb shell pm uninstall --user 0 com.xiaomi.market #小米应用商店，请在此下载安装Google Play（别的商店代替）、Google Play）

```

===（手动重启手机）===


------


# <a id="no-4"></a>四、小米系统扩展用法：

### 1. 「可选」打开你的网络代理，在Google Play下载：
Google电话、Google短信、Google Photo、微信（Play版微信需要下载小程序扩展）等软件。

### 2. 必备浏览器：
- Firefox浏览器 添加ad扩展（国内IP不可用此功能）；
- 三星浏览器 添加屏蔽广告扩展（在Google Play里下载扩展），如果无法安装，清除 浏览器 数据并重新设置。
  国内环境如何安装三星浏览器插件：
  - 在浏览器地址栏输入：internet://debug/
  - 此时在点击浏览器设置，翻到最底下就会出现一个Debug settings选项，点击进去
  - 找到选项：Feature variation test，点击进入 。点击Sales code选项，翻到最底下点击Other，输入：TGY，确认。 点击Country code选项，翻到最底下点击Other，输入：Hong Kong，确认。 点击Country iso code选项，翻到最底下点击Other，输入：HK，确认。
  - 关闭三星浏览器，去任务卡片中划掉它，其实就是重启一下。
  - 然后点击设置中的广告拦截，此时就可以点击下载拦截器了。如果下载不了（新版本需要在Google Play里面下载插件），就用直接安装广告拦截软件的APK的方法（Samsungbrowser V30.0.0 已验证）：
      - AdGuard for SamsungBrowser： https://github.com/fyonecon/clean_hyperos/releases/download/HyperOS3-20260428/AdGuard_samsung.browser_2.8.0.apk.7z （需要把“.7z”后缀直接删掉即可是对应.apk文件。）
      - ABP for SamsungBrowser：https://github.com/fyonecon/clean_hyperos/releases/download/HyperOS3-20260428/ABP_samsung.browser_2.5.7.apk.7z （需要把“.7z”后缀直接删掉即可是对应.apk文件。）

### 3.1 推荐几个安卓应用商店：
- 应用汇（国内）：https://www.appchina.com
- 应用宝（国内）：https://sj.qq.com

### 3.2 应用列表及权限管理，（同 电池管理、联网管理等）：
如果需要从“手机设置App”进入权限和应用列表来管理应用，需要下面系统App组件（从长按App图标进或者使用第三方管理程序这不需要）：
```
com.miui.securitycenter #安全中心

com.lbe.security.miui #MIUI权限管理（关闭系统优化时可选）
```

### 3.3 手机NFC：
小米的NFC开卡居然是收费20RMB，iPhone就不需要。

需要下面系统App组件：
```
com.miui.securitycenter #安全中心

com.miui.tsmclient #小米智能卡

com.miui.wmsvc #似乎与快应用的信息服务有关（有人说与NFC充值也有关）

com.miui.nextpay #卡包网页组件
```

### 3.4 小米消息推送：
需要有下面两个系统app组件：
```
com.xiaomi.xmsf

com.xiaomi.xmsfkeeper
```

### 4. 关于“国内 OAID”和“Google ADID”的说明：
- 这两个ID都可以跨App追踪用户，实现用户“隐私与广告”跨App互通。
- 删除OAID：adb删除“com.miui.securitycenter”即可永久关闭OAID。
- 删除Google ADID：在“Google Services”软件里找“Ads”，选择“删除”即可永久关闭ADID。
- 设备指纹ID：无需关心。
- App列表权限：这个不管你优不优化国内任何安卓系统，App都能在不需要用户同意的情况下获取到App列表，所以无需在意，除非你用国外安卓系统。微信、京东、拼多多没有获取应用列表权限，其他App中90%都在暗中获取应用列表权限。

证实：
> ⚠️ 检查OAID及ADID值：
https://github.com/fyonecon/clean_hyperos/releases/download/HyperOS3-20260428/OAID.apk.7z （需要把“.7z”后缀直接删掉即可是对应.apk文件。）

> ⚠️ 无授权的情况下查看应用列表：
https://github.com/fyonecon/clean_hyperos/releases/download/HyperOS3-20260428/AppListViewer.apk.7z （需要把“.7z”后缀直接删掉即可是对应.apk文件。）


### 5. 提升手机系统流畅度说明：
- 关闭“系统优化”后，系统的动画和页面切换效果将变为安卓原生的，即使是60Hz，也比“小米自带动画特效”流畅很多，特别是在低端机上表现特别明显。
- 小米桌面App真的卡，一个桌面App有可能占800MB的ram，特别是在多系统用户空间下特别卡。我使用第三方桌面lawnchair https://lawnchair.app/ （需在该App设置里手动关闭软件禁用才能设置默认桌面），虽然牺牲了手势操作（启用第三方桌面小米手势就会用不了，只能用三大键，这个真的很鸡贼），但是换来了操作流畅。

### 6. 如何更新手机系统自带Webview：
- 打开LibChecker软件 -- 找到 webview -- 选择“打开Launch” -- 选择“Webview DevTools” -- 切换到“Home” -- 点击右上三角，选择"Check for Webview updates" -- 软件自动跳到Google Play商店，点击更新即可。
- 如果你直接打开Google Play来更新Webview，除了安装 Webview Dev 版这个办法，是不能直接更新自系统带版的，所以只能按照上面步骤曲线更新Webview。

### 7. 如何安装 李跳跳（针对国产软件的快速跳过开屏广告等）：
- 下载：https://www.downkuai.com/android/144622.html ；
- 安装、打开 李跳跳，不做任何操作 -- 回到桌面，并长按“李跳跳”图标调出“关于” -- 在“关于”软件界面的最底部有个“···”按钮，点击并允许（这是小米拦截了软件的辅助功能，需要手动允许） -- 进入手设置里的“辅助设置Accessibility” -- “通用” -- “已下载软件” -- 打开李跳跳即可。 
- 注意，这只是跳过广告，不能阻断广告。阻断广告请参考本章节第11条。

### 8. 开启Shizuku：
- 安装 Shizuku（ https://github.com/RikkaApps/Shizuku/releases ）；
- 登录小米账号com.xiaomi.account + 有安全服务com.miui.securitycenter软件；
- 重启手机；
- 在开发者模式的“USB调试、USB调试（安全模式）、无线调试”这3个按钮；
- 打开 Shizuku 按照步骤完成授权。

### 9. 多用户系统（有条件的系统隔离度高）：

什么是“多用户”：设置-其他设置-用户-（多用户：包括访客用户）。

什么是“分身用户”：设置-密码安全-手机分身-（分身用户）。

如何设置“多用户”锁屏密码：无法直接修改密码，不管系统收否关闭或开启系统优化，都无法直接设置锁屏密码，但是可以曲线设置：进入目标用户系统-设置-主题-指纹识别样式-（设置锁屏密码）。

注意，锁屏密码设置后就不可以更改了，此处你要是设置了指纹，那么这个指纹可以解锁主用户的锁屏，请不要设置多用户的指纹解锁，如果设置了，可以在主用户的“密码与安全”将这个指纹删除。

如何设置“分身用户”锁屏密码：设置-密码安全-手机分身-（管理）

高级玩法：

  - ⚠️“分身用户”的SecurityCore删除后会自动恢复，而“多用户”不会。

  - ⚠️“分身用户”在使用几天后可能遇到锁屏密码失效的问题（会彻底丢失资料）。建议使用“Multi User 多用户”，极不建议使用“分身用户”。

  - ⚠️“多用户”的第一个系统可能在关闭“系统优化”后可能只能从Play商店安装app，无法从比如文件夹安装App。解决办法：开几个用户尝试留下功能正常的多用户。

  - ⚠️⚠️关于在主系统或者有“访问正在运行程序”权限的App可以通过“进程残留、RAM残留、UsageStats”跨系统访问到“多用户”系统里面运行过的App的名单。【消除办法是：在使用完“多用户”后，请重启一次手机或者锁屏一次手机，避免HyperOS安全机制缺陷造成的跨系统App名单泄露】。这是使用HyperOS中总结的系统Bug，无法确定是否真实存在，也可能不是后门或者不是隐藏Api。如果主系统中App都是安全可信权限的，可以忽略上面内容。

  - “多用户”下建议开启内存扩展，可以后台挂更多程序，切换系统也可以在个自系统里持续正常运行。

### 10. 激活GMS消息推送（FCM）：

现在在大陆iOS中，除了Gmail消息可以正常接收，其它应用的消息推送全挂了（一些著名App除外）。

在Android中，激活GMS消息推送（FCM）后可以正常接收。步骤：
- 梯子环境下，在 Google Play 商店下载、安装、注册App；

- 在电话里输入
    ```
    *#*#4263#*#*
    ```
    查看“Connection Status”是否是“Connected”，是则已激活；

- 保证“省电策略会不要杀掉 GMS 后台”，Google Play和对应App要加入到“不限制后台”。
- 如果注册了FCM的app消息推送出现不及时的情况，锁屏10s+再解锁屏幕一次就好了。

### 11. 利用“VPN DNS”来自定义App联网规则（屏蔽广告、阻断联网、添加机场）：

下载BlockADs（开源+免费）：https://blockads.pwhs.app 。

备用地址：https://github.com/pass-with-high-score/blockads-android/releases 。

如何设置：

模式选本地，VPN设置在“手机系统设置”里设置成“始终开启VPN，未开启VPN时阻断所有连接”；我导入crt证书时发现小米并不能手动导入成功，可能是因为之前卸载了某个校验软件导致的，这个问题暂时保留。

主要特性：

- 屏蔽App广告；
- 阻断App联网（包含用户App和系统App。 小米手机管家com.miui.securitycenter 中有的App不能被阻断联网，在这里可以利用BlockADs全部阻断掉。注意“GMS服务、Google Play、微信”等最好不要阻断联网。）；
- 可以添加机场账号，但是与别的VPN软件不能同时开启；
- 你可以用这个软件阻断你不想卸载和卸载会卡米的App的联网，因此如果你是基于Android17的OS4，强烈推荐此方法。


------


# <a id="no-5"></a>五、恢复已删除App：

⚠️恢复软件后需要手动重启手机一次。

### 1. 恢复已删除的预装应用举例：

> adb shell cmd package install-existing （应用包名）

举例：

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

adb shell cmd package install-existing com.xiaomi.xmsf #小米服务1（微信消息、Mipush）

adb shell cmd package install-existing com.xiaomi.xmsfkeeper #小米服务2（微信消息、Mipush）

adb shell cmd package install-existing com.miui.powerkeeper #电量和性能（智能杀后台应用，后台保活相关）

adb shell cmd package install-existing com.android.camera #小米相机

adb shell cmd package install-existing com.miui.core #（系统SDK API）

adb shell cmd package install-existing com.miui.home #小米桌面

```

### 2. 禁用和恢复禁用的命令（在OS4中的唯一用法，OS1、OS2、OS3中不推荐。）：
```
禁用：
adb shell pm disable-user --user 0 [应用包名]

恢复禁用：
adb shell pm enable [应用包名]

```


### 3. 给手机导入导出文件示例：
```
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

```


------


# <a id="no-end"></a>End 吐槽：

小米系统给人的感觉就是：
> 功能有但不完整，价格低但缺维护，有特色但没创新，有创新但全打散。

对比iOS和OneUI：
> 要安全无隐私，要功能不完整。


------