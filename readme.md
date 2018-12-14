## 关于乾坤塔
乾坤塔是基于 Android 系统原生的设备管理员相关功能开发的，因为开发者手机没有root过的手机，因此无法预测到在已经root的手机上会出现什么样的问题。并且由于开发者手里仅有pixel 2、华为P10、三星等手机进行测试，也无法预估在其他机型上会出现什么问题。所以请谨慎使用。

## 乾坤塔设备管理员模式使用配置方法(以下内容大部分摘抄冰箱使用文档)

#### 国产手机及三星系统请注意：

国产手机系统时常添加各种中国特色功能，因此其与设备管理员模式的兼容性或多或少存在一些问题，常见如下：

- 三星有可能被系统锁定密码（目前收到反馈大约二十万分之四），请参考[冰箱文档](https://github.com/heruoxin/Ice-Box-Docs/blob/master/Device%20Owner%20%E4%B8%89%E6%98%9F%E7%89%B9%E5%88%AB%E8%AF%B4%E6%98%8E.md)
- 每次冻结 App 弹出卸载提示，解冻弹出权限请求（华为、锤子）
- 通知栏闪烁「设备管理员已开启，点击关闭」（OPPO、VIVO）
- 自带的双开无法使用（华为、MIUI）
- 偶尔刚解冻的 App 无法联网，关掉 App 重开即可（一加等）
- 索尼建议在升级 9.0 之前先设置好冰箱，9.0 系统添加了隐藏帐号难以删除，如已升级，建议使用下面的免电脑二维码设置（已授权的不受影响）。


如不能接受上述问题，请谨慎使用

设备管理员模式则不需要反复连接电脑设置，一次配置，终身有效，重启或升级系统都没有影响。

### 设备管理员设置步骤

0. 首先确保您的手机 Android 版本大于等于 5.1，您已经知道如何操作 [adb](https://sspai.com/post/23509) 命令。并且已经阅读完整篇教程。
1. 索尼手机取出手机 SIM 卡；小米用户请开启「USB 调试（安全设置）」关闭「MIUI 优化」。
2. 进入手机「设置 - 帐户」，删除 #所有# 的帐户，包括你的 Google/小米/华为等系统帐号（之后可以再登录回来）。
3. 如果您之前设置过多用户或手机自带访客模式、应用双开等，也需要一并关闭或删除（之后可以打开）。
4. 在电脑上执行（手机终端模拟器不行）`adb shell dpm set-device-owner com.qiankuntower.app/.DOR`
5. 如果显示 Success 之类的字样，那么即可打开乾坤塔使用，也可以把之前删除的帐号加回来了。

#### 其他事项

adb 工具可以在下列地址下载：

- Google 官方地址 （[Win](https://dl.google.com/android/repository/platform-tools-latest-windows.zip) [Mac](https://dl.google.com/android/repository/platform-tools-latest-darwin.zip) [Linux](https://dl.google.com/android/repository/platform-tools-latest-linux.zip)）

- 国内[百度盘](https://pan.baidu.com/s/1q9SWiK9Loivyt6zvr98seQ)


### 常见问题：

#### 未设置成功？

- 问：提示 “adb不是内部或外部命令 也不是可运行程序”
- 答：建议先学习有关电脑操作命令行的基础用法。

- 问：提示 “error: no devices/emulators found”
- 答：手机未连接上电脑，请检查手机是否开启 USB 调试，电脑是否正确安装了对应的驱动，有没有QQ/管家/杀毒软件阻止了连接。

- 问：提示 “Not allowed to ... already several accounts on the device”
- 答：第 1 步的账户没删干净，请注销您手机上所有的账户，包括 Google 账号和系统自带的如小米账户、华为账户等，索尼手机请拔 SIM 卡重启。

- 问：提示 “Not allowed to ... already several users on the device”
- 答：第 2 步的多用户没删干净，请删除或关闭所有多用户/访客模式/应用双开。

- 问：提示 “Trying to set the device owner, but device owner is already set.”？
- 答：您已设置其他 app 为设备管理员。一台手机上只能有一个设备管理员。

- 问：MIUI 用户提示 “Neither user xxx nor current process has android.permission.MANAGE_DEVICE_ADMINS”
- 答：MIUI 用户请手动在系统设置- 开发者设置里，开启「USB 调试（安全设置）」，如仍不可以请关闭 MIUI 优化。


#### 已设置成功，但是？

- 问：设置完成后手机通知栏出现提示「手机被管理」，这是正常的吗？
- 答：正常的。

- 问：我不想用了，怎么解除乾坤塔的权限？
- 答：请先解封所有的应用，然后到乾坤塔设置里点击「解除管理员权限」，确认后即可解除授权。或者电脑执行命令`adb shell dpm remove-active-admin com.qiankuntower.app/.DOR`
