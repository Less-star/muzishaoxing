# 黑苹果之登陆APP Store（设备内建）

## 为什么需要设备内建？

- 黑苹果后登陆APP Store会提示：“无法验证您的设备或电脑,请联系技术支持寻求帮助”或者“发生未知错误”等各种错误情况,这是因为你的网卡没有内建.
- 这里简单说下网卡内建,网上有很多方法,改DSDT什么的,对于我等小白来说,实在深奥,这里就分享一个比较简单而且实用的方法.

## 我是否需要内建？

- 首先用Hackintool查一下网卡内建信息
  - [Hackintool 中文版 (黑苹果必备工具箱](https://github.com/headkaze/Hackintool/releases)

![图片](https://mmbiz.qpic.cn/mmbiz_png/icVMsVyPSD2klb8ibZdia1L0YEjG93fFMGtAMyJAiaHjweYUo84eGq2zLwuibdOos7yibVNde0ULezm7TYgrIaicXic7CQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

- 上图标记处en0内建没有☑️就是代表网卡没有内建，则需要以下内容
  - 如果有就不要往下看了，没啥意思

## 网卡内建

1. 打开访达左上角-前往-前往文件夹-输入以下地址：

   > /Library/Preferences/SystemConfiguration/NetworkInterfaces.plist

   ![](https://mmbiz.qpic.cn/mmbiz_png/icVMsVyPSD2klb8ibZdia1L0YEjG93fFMGtB3b3uF91TjxKdOMCZVGqjgB8qR50w8J1ic8WiaqJQkOJ2l17TBjmKljg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

   - 找到并删除NetworkInterfaces.plist（可能需要打开显示隐藏文件）

2. 在系统设置偏好的”网络””里删除所有网络连接
   ![图片](https://mmbiz.qpic.cn/mmbiz_png/icVMsVyPSD2klb8ibZdia1L0YEjG93fFMGtVgkKRCQ1ZHC5D4NlGUv3iajmbyhgnQ2bzh2Vz7rblqjXUgYFmTyicv6g/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

3. 重新启动

4. 查看或重新在系统设置偏好的”网络”里加所有网络连接（这条一般系统会自动完成）

5. 这时候在进入上一步你会发现网卡内建已经☑️完成

6. 如果这时候你还是登陆不上iCloud，请参考：仿冒以太网

   

## 设备内建

- 如果此上述效果不好使或者你想内建其他设备
  - 例如：NVMe磁盘被识别外置改内置

  - 可以采用以下设置

- 打开Hackintool-PCIe查找该设备PCI路径

![图片](https://mmbiz.qpic.cn/mmbiz_png/icVMsVyPSD2klb8ibZdia1L0YEjG93fFMGtB5QzpT9lXn95Oq9ng3iagmvbLAPXFzLPAtmsNxPYF0DMDAoJnzwzBeQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

> 点击后会复制一串代码将其填写到配置表文件

- OC引导配置表路径：EFI-OC-config.plist
- 使用OpenCore Configurator打开此文件
  - [OpenCore Configurator下载地址](https://macwk.com/soft/opencore-configurator)

- 左侧是上图设备路径代码-右侧是内建代码

![图片](https://mmbiz.qpic.cn/mmbiz_png/icVMsVyPSD2klb8ibZdia1L0YEjG93fFMGt366E3IFibHAfU7ASO97KAh50hIicklVmbjCh1L842JqqqomNcfRM2rNA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

```
built-in   01   data
```

- 填写完成后保存重启即可发现，相应设备已经完成内建。

## 仿冒以太网

- 部分设备换需要仿冒以太网方可登陆请参考链接
  - [仿冒以太网](http://ocbook.tlhub.cn/13-%E4%BB%BF%E5%86%92%E4%BB%A5%E5%A4%AA%E7%BD%91%E5%92%8C%E9%87%8D%E7%BD%AE%E4%BB%A5%E5%A4%AA%E7%BD%91BSD%20Name/)

## 最后阐述

- 完成上述操作APP Store ，iCloud基本可以正常登陆了
  - 如果还不能登录iCloud或者iMessage、Facetime则需更换新三码
   - 新注册的账号有很大几率无法登陆iMessage、Facetime这是正常的
    - 自购对应白果三码填入百分百解决

- 另外吧，黑的就是黑的，不完善别较劲