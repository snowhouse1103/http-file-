## http协议与file协议的区别
1. File协议主要是用于访问本地计算机的文件资源，没有网络交互，无法实现跨域。file协议对应的也有类似于http的远程访问，就是ftp协议。
2. http协议工作于客户端-服务器架构上，浏览器作为http客户端通过url向http服务器端发送请求，服务器接收到请求后，向客户端发送请求。在本地架设Http服务器，相当于将本机作为一台http服务器，然后通过localhost访问的是你本机服务器，解析http协议的请求然后向浏览器返回资源信息。开放端口之后，别人也可以通过http访问到你电脑里的页面，但是file协议做不到。
3. 简单来讲，file只是简单请求了本地文件，将其作为一个服务器未解析的静态文件打开。而http是在本地搭建了一个服务器再通过服务器去动态解析拿到文件。我们所开发的html文件最后必定是会以网页的形式部署在服务器上，通过http协议访问，所以我们开发中也尽可能模拟线上环境，架设本地服务器，来避免file协议与http协议实现过程中的某些差异，如某些API的差异、跨域请求的差异等。
## HTTP请求 vs AJAX请求
两者本质区别：
1. AJAX通xmlHttpRequest象请求服务器服务器接受请求返数据实现刷新交互；普通http请求通httpRequest象请求服务器接受请求返数据需要页面刷新
2. AJAX请求头会多一个x-requested-with参数，值为XMLHttpRequest。  String requestType = request.getHeader("X-Requested-With"); 
