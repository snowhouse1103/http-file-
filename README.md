## http协议与file协议的区别
* File协议主要是用于访问本地计算机的文件资源，没有网络交互，无法实现跨域。file协议对应的也有类似于http的远程访问，就是ftp协议。
* http协议工作于客户端-服务器架构上，浏览器作为http客户端通过url向http服务器端发送请求，服务器接收到请求后，向客户端发送请求。在本地架设Http服务器，相当于将本机作为一台http服务器，然后通过localhost访问的是你本机服务器，解析http协议的请求然后向浏览器返回资源信息。开放端口之后，别人也可以通过http访问到你电脑里的页面，但是file协议做不到。
  > 简单来讲，file只是简单请求了本地文件，将其作为一个服务器未解析的静态文件打开。而http是在本地搭建了一个服务器再通过服务器去动态解析拿到文件。我们所开发的html文件最后必定是会以网页的形式部署在服 务器上，通过http协议访问，所以我们开发中也尽可能模拟线上环境，架设本地服务器，来避免file协议与http协议实现过程中的某些差异，如某些API的差异、跨域请求的差异等。
## HTTP请求 vs AJAX请求
两者本质区别：
1. AJAX通xmlHttpRequest象请求服务器服务器接受请求返数据实现刷新交互；普通http请求通httpRequest象请求服务器接受请求返数据需要页面刷新
2. AJAX请求头会多一个x-requested-with参数，值为XMLHttpRequest。  String requestType = request.getHeader("X-Requested-With"); 
  > 是否需要用本地服务器打开 html 分几种情况：html 中是否是纯静态模板页，纯静态模板页指页面内没有“请求服务器”获取数据，展示的是为了布局占位临时写的“假”数据。比如，“姓名”、“年龄”，后端数据还没完成，前端先写模板页，随便写“姓名： 张三”、“年龄：18”，先把页面布局和样式完成，这个阶段不需要开启本地服务器。html 中引用的静态资源是否需要构建工具打包编译，比如 js 使用了 ES6 新特性、css 使用了 less 编写等，这时可能需要使用 Webpack 等工具进行编译。这时，一般需要启动一个本地 node.js 服务去执行编译和预览 开发中是否用到“实时刷新，同步预览”如果开发中修改文件不想每次都点击刷新或按 F5，保存时自动刷新，可以借助一些工具，比如 livereload、browserSync 等。用这些工具，需要启动一个本地服务开发中是否用到多终端调试如果开发的静态页面想在某品牌手机真机上看显示效果，调试兼容性问题，除了最笨的把页面和静态资源发送到手机上，还以可以起一个本地服务，电脑与手机连接到同一 Wifi 下，用手机访问本地服务 loalhost 对应的内网 ip 地址即可。

参考文献：https://blog.csdn.net/weixin_42839080/article/details/82833111
参考文献：https://blog.csdn.net/u014465934/article/details/89212304
