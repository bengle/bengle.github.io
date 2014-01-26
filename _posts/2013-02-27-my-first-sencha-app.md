---
layout: default
title: Sencha touch学习
---
# {{ page.title }}
{{ page.date | date_to_string }}

### 第一步 下载开发包

到sencha官网上填写邮件地址即可获得sencha的开发包：http://www.sencha.com/。解压开发包得到一个文件夹，里面很多文件包括源文件、文档、例子、例子的资源以及版本和发布信息等。
	sencha Cmd安装略显麻烦，需要先安装compass，而安装compass又需要先安装ruby，好在mac上ruby是默认装好的。安装好Cmd之后还要配置它的路径到系统的环境变量$PATH中，上网查了下只要在主目录下建一个.bash_profile文件里面添加export PATH=$PATH:/Users/bengle/bin/Sencha/Cmd/3.0.2.288这么一行命令之后source .bash_profile就可以了，但是试了还要几次始终无效，真是蛋碎了一地。。。最后直接运行这个命令算是暂时成功了。用户可以尝试把这个命令添加到/etc/.profile中去。
	
### 第二步 一个应用

接下来就可以根据官网上给出的getting start资料开始sencha的学习之旅了。按着教程的来运行sencha -sdk mywork/touch-2.1.1 generate app myFirslstSencha myFirslstSencha命令生成了我的第一个sencha应用，鸡冻了！
打开文件夹找到一个index.html的文件，通过本地apache服务器用浏览器打开可以看到默认生成的应用。其中app文件夹里面放置的是应用的MVC层的js文件，resources文件夹里面放置的是图片、css等，touch文件夹里面放的是sencha开发sdk文件。另外有app.js是入口文件里面调用app文件夹中的模块文件。packager.json是应用打包的配置文件，具体如何配置后面再说。

### 第三步 打包应用

应用已经生成，我们还可以用浏览器直接查看，那么怎么在模拟器上验证呢？很简单，运行命令：sencha app package run packager.json 即可调用模拟器查看运行结果。
验证完毕接下来就要打包应用啦！不过打包之前我们需要先了解一下packager.json这个配置文件。
 
	{ 
	    "applicationName": "<AppName>", 
	    "applicationId": "<AppID>", 
	    "outputPath": "<AppPackageOutputPath>", 
	    "iconName": "<AppIconName>", 
	    "versionString": "<AppVersion>", 
	    "webAppPath": "<PathToWebApp>", 
	    "configuration": "<Release | Debug>", 
	    "platform": "<iOSSimulator | iOS>", 
	    "deviceType": "<iPhone | iPad | Universal>", 
	    "certificateAlias": "<(Optional)CertificateAlias>", 
	    "orientations": [ 
	        "portrait", 
	        "landscapeLeft", 
	        "landscapeRight", 
	        "portraitUpsideDown" 
	    ] 
	} 
	
其中主要的配置项如下：

	- AppName 为 “Sencha Touch 2 Packaging”则AppID 为 “com.Sencha.Touch2Packaging”。注意:  App ID 需要与你在 Xcode的Identifier field输入的相同 ；
	- versionString是application的版本；
	- webAppPath是用来打包的web application路径；
	- configuration是指定创建出程序的类型: Release or Debug；
	- platform是制定创建出程序的运行方式 iOS 模拟器还是iOS设备；
	- deviceType是指定设备类型.可选项: iPhone：用于 iPhone 设备 ，iPad：用于iPad 设备 ，Universal：可用于iphone和iPad二者；
	- certificateAlias是这是一个非必选项.，你可以指定一个Certificate Alias来给你的app命名；
	- orientations是一个可选的配置项. 你可以给app指定方向，可选项包括: “portrait”, “landscapeLeft”, “landscapeRight” and “portraitUpsideDown”；

配置得当之后使用sencha app build [testing | production | native]命令打包应用就可以得到我的第一个sencha应用啦！生成的是一个.app文件夹，上网查一下就可以用iTunes生成.ipa的可安装文件，hoho！