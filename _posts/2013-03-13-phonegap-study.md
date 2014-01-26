---
layout: default
title: phonegap创建一个ios应用
---
# {{ page.title }}
{{ page.date | date_to_string }}

- 到<a href="http://phonegap.com/download/" target="_blank">http://phonegap.com/download/</a>下载最新版phonegap开发包；
- 创建一个空的文件夹（MyPhonegapApp），命名为你的应用名称；
- 打开终端，输入命令：

		cd /Users/chenhaojie/Desktop/phonegap-phonegap-26d211b/lib/ios/bin
		./create /Users/chenhaojie/Desktop/MyPhonegapApp com.sosceo.MyPhonegapApp MyPhonegapApp
- 命令解释：

		1. /Users/chenhaojie/Desktop/phonegap-phonegap-26d211b/lib/ios/bin/ 此为你的phonegap->lib->ios->bin->create在磁盘上面的路径。
		2. /Users/chenhaojie/Desktop/MyPhonegapApp 此为创建的空文件夹MyPhonegapApp（存放你要创建的项目的文件夹个人建议和你的项目名称保持一致）。
		3. com.sosceo.MyPhonegapApp 这是很熟悉的反域名命名方式，（类似在xcode创建项目的时候要填写的identifier（项目的唯一描述，可以用这个来配配置你项目的URLScheme，用来提供给第三方软件打开你的应用））。
		4. MyPhonegapApp项目名称。