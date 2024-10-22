# 微信视频号下载器

又是一个轮子，不过用起来更简单些。

## 241022 更新

当视频被删除时没有正确地显示「被删除」而是一直处于加载中状态。
下载按钮修改成和其他操作按钮相同的样式。

## 241016 更新

前一个版本又下载不了，改回在页面直接下载又正常了，是和微信客户端版本有关吗，对这块不了解。
如果 241016 这个版本用不了，可以试试其他版本。
我目前微信客户端版本是 `Weixin 3.9.12.17`，可以正常下载的。

## 241011 更新

应该是视频号又改版了，不能直接在页面下载了。改成点击下载按钮复制视频链接到粘贴板，然后到谷歌或其他浏览器打开下载。
另外测试了很多视频都可以直接下载，没有加密了。所以如果有加密视频，新版本可能会下载失败。

> 在页面直接下载，理论上还是能实现，实现上要麻烦许多，后面再研究。

## 使用说明

下载二进制文件，**以管理员身份运行**。


第一次运行会提示 「您还未安装证书，请在浏览器打开 http://127.0.0.1:2023 并根据说明安装证书」

![首次打开](assets/screenshot3.png)


根据提示在浏览器打开 http://127.0.0.1:2023 ，会出现如下页面

![证书下载+说明](assets/screenshot4.png)


点击页面上「SunnyRoot 证书」会自动下载证书文件。下载成功后，双击安装，并按如下要求，放置在「受信任的根证书颁发机构」文件夹

![证书安装步骤](assets/screenshot6.png)


关闭之前打开的终端，并重新「以管理员身份运行」，下面的截图就说明证书安装成功，可以正常使用了。

![正常使用](assets/screenshot7.png)


打开微信 PC 端，点击需要下载的视频，在视频下方的操作按钮一栏，会多出一个下载按钮，如下所示

![视频下载按钮](assets/screenshot1.png)


点击即可下载视频。下载成功后，会在上方显示已下载的文件。

![视频下载成功](assets/screenshot2.png)

## 开发说明

先以 管理员身份 启动终端，然后 `go run main.go` 即可。

## 打包

```bash
go build -o wx_video_download.exe main.go
```

打包后可以使用 `upx` 压缩，体积可以从 17MB 压缩到 5MB。

## 其他

此程序大部分参考自以下项目代码

https://github.com/kanadeblisst00/WechatVideoSniffer2.0

此程序的核心实现依赖以下库

https://github.com/qtgolang/SunnyNet
