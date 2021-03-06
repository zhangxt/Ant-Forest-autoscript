# 简介

基于 Autojs 的蚂蚁森林自动收能量脚本，采用 4.0.5Alpha 版本开发。解锁模块参考自：https://github.com/e1399579/autojs

*注意：新版本因缺乏样本，测试不够全面，麻烦大家及时反馈BUG，如需使用旧版，直接下载 old 中的文件*

- 2019/1/31 
  - ~~发现识别能量罩时采用的函数不合适~~（使用了同步获取 toast 的方法，会卡住，已修正）
  - ~~帮助好友收取时，默认所有能量球都各点击一遍，效率太低~~（已修正）
  - 重构代码，添加注释

- 2019/2/1
  - ~~Toast 监听器超过10过导致报错~~（已修正）
  - ~~帮助好友收取时有时候会失败~~（因为控件下方文字闪烁导致，已修正）
  - 不限制监听器数量并且每次运行完成后清空监听器
  
- 2019/2/2
  - ~~自己的倒计时减为0时会结束收取而不是立马收取下一次~~（已修正）
  
- 2019/2/5
  - ~~实际运行中安卓7.0以下会报错~~（已修正）

# 使用

下载安装 [Autojs](https://github.com/hyb1996/Auto.js) 之后把整个脚本项目放进 __"/sdcard/脚本/"__ 文件夹下面。运行项目或者 main 即可。

# 功能

- 自动匹配不同系统下自动化的方式，安卓7及以上通过无障碍服务模拟操作，以下版本通过 root 权限模拟操作；
- 自动识别屏幕锁定方式并根据配置的密码解锁，支持图形解锁，PIN解锁，混合密码解锁；
- 识别自己能量球的倒计时，和好友列表中的倒计时做对比，取最小值作为下次收取的等待时间；
- 识别好友能量罩，下一次收取时跳过开启能量罩的好友；
- 根据设置选择是否帮助好友收取能量；
- 收取完毕后悬浮框显示收取的能量数量。

# 配置

打开 config.js 后可以看到如下配置：

```javascript
var config = {
  color_offset: 4,
  password: "52897",
  help_friend: true,
  max_unlock_retry: 3,
  max_collect_repeat: 20,
  max_collect_wait_time: 20
};
```

其中：

- color_offset：设置颜色识别的偏移量，如果识别失败可以尝试增加该值；
- password：手机解锁密码，如果是图形解锁则为图形经过的点对应的数字；
- help_friend：设定是否帮助好友收取能量；
- max_unlock_retry：解锁最大尝试次数；
- max_collect_repeat：脚本重复收取的最大次数；
- max_collect_wait_time：等待好友收取能量倒计时的最大值。

# 注意事项

解锁仅支持：

- 具有ROOT权限的安卓5.0及以上版本
- 没有ROOT权限的安卓7.0及以上版本

# 目前存在的问题

- 某些未ROOT设备无法解锁混合密码
- Autojs 在锁屏状态下由于软件优先度被降低导致 sleep() 函数时间不准确
- 由于MIUI的布局和原生差别有点大，小米手机无法解锁，希望哪位朋友能帮忙开发一下，添加到 Unlock.js 的 Device 里面即可

