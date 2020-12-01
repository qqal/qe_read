# 安卓企鹅阅读
记录一下过程
###1.安卓抓包工具  
HttpCanary 小黄鸟

###2.安卓用户抓包Secrets格式如下所示  
{"ywsession":"填写你的ywsession信息","Cookie":"填写你QQREADHEADERKEY的cookie","Connection":"keep-alive","Content-Type":"application/json","Accept":"\*/\*","Host":"mqqapi.reader.qq.com","User-Agent":"你抓到的UserAgent","Referer":"Referer链接","Accept-Language":"zh-cn","Accept-Encoding":"gzip, deflate, br","mpversion":"这个安卓和IOS的不一致，自己填"}@QQReadtimeurlVal@{"ywsession":"填写你的ywsession信息","Cookie":"填写你QQREADHEADERKEY的cookie,长一点的，带openid的","Connection":"keep-alive","Content-Type":"application/json","Accept":"\*/\*’","Host":"mqqapi.reader.qq.com","User-Agent":"你抓到的UserAgent","Referer":"Referer链接","Accept-Language":"zh-cn","Accept-Encoding":"gzip, deflate, br","mpversion":"这个安卓和IOS的不一致，自己填"}

###3.利用上面的样例 打开https://www.runoob.com/try/try-cdnjs.php?filename=tryjson_stringify  格式化json数据，一共三段

#### 样例：  
{"ywsession":"111","Cookie":"ywguid=111;ywkey=11;platform=android;channel=mqqmina;mpVersion=0.30.0","Connection":"keep-alive","Content-Type":"application/json","Accept":"\*/\*","Host":"mqqapi.reader.qq.com","User-Agent":"111","Referer":"https://appservice.qq.com/1110657249/0.30.0/page-frame.html","Accept-Language":"zh-cn","Accept-Encoding":"gzip, deflate, br","mpversion":"0.30.0"}@https://mqqapi.reader.qq.com/mqq/样例=-1@{"ywsession":"11","Cookie":"ywguid=11;ywkey=11;platform=android;channel=mqqmina;mpVersion=0.30.0;qq_ver=8.4.18.4945;os_ver=Android 10;mpos_ver=0.30.0;platform=android;openid=11","Connection":"keep-alive","Content-Type":"application/json","Accept":"\*/\*","Host":"mqqapi.reader.qq.com","User-Agent":"1111","Referer":"https://appservice.qq.com/yangli","Accept-Language":"zh-cn","Accept-Encoding":"gzip, deflate, br","mpversion":"0.30.0"}

### 多账号格式,直接换行就行  
账号1的qqreadheaderVal@qqreadtimeVal@qqreadtimeheaderVal  
账号2的qqreadheaderVal@qqreadtimeVal@qqreadtimeheaderVal  
账号3的qqreadheaderVal@qqreadtimeVal@qqreadtimeheaderVal  

）
