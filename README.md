# 安卓企鹅阅读
记录一下过程
###1.安卓抓包工具  
HttpCanary 小黄鸟

###2.安卓用户抓包Secrets格式如下所示  
{"common":{"appid":1450024393,"areaid":5,"qq_ver":"8.4.10.4875","os_ver":"Android 10","mp_ver":"1.0.2","mpos_ver":"1.20.0","brand":"Xiaomi","model":"MI 8","screenWidth":393,"screenHeight":801,"windowWidth":393,"windowHeight":747,"openid":"3557920122AE63FB704655CA9F955FEF","guid":xxxxxxx,"session":"xxxxxxx","scene":3001,"source":-1,"hasRedDot":"false","missions":-1,"caseID":-1},"dataList":[{"click1":"qqauthorize_addRCS_succ_C","click2":"qqauthorize_addRCS_get_C","route":"pages/book-detail/index","refer":"pages/book-category/index","options":{"bid":"26617976"},"dis":1609900701212,"ext6":93,"eventID":"bookRead_dropOut_shelfYes_C","type":"click","bid":"26617976","ccid":1,"bookStatus":0,"bookPay":0,"chapterStatus":0,"from":"bookLib2_bookList_bookClick_C_1_26617976"}]}@QQReadtimeurlVal@{"ywsession":"填写你的ywsession信息","Cookie":"填写你QQREADHEADERKEY的cookie,长一点的，带openid的","Connection":"keep-alive","Content-Type":"application/json","Accept":"\*/\*’","Host":"mqqapi.reader.qq.com","User-Agent":"你抓到的UserAgent","Referer":"Referer链接","Accept-Language":"zh-cn","Accept-Encoding":"gzip, deflate, br","mpversion":"这个安卓和IOS的不一致，自己填"}
###3.准备工作获取
打开HttpCanary,进入QQ小程序，搜索企鹅阅读，之后打开抓包工具，再选择一本书记住阅读不要超过十秒，五秒最佳。关闭抓包工具。

###4.利用上面的样例，将第3步得到的数据替换到格式里面 打开https://www.runoob.com/try/try-cdnjs.php?filename=tryjson_stringify  格式化json数据，一共三段
![image](https://github.com/llllcccjjj/qe_read/blob/main/img/1.png) 这是一个使用图 
先格式第一段，再格式第三段
第二段的打开抓包工具搜索ReadtimeWithBid
![image](https://github.com/llllcccjjj/qe_read/blob/main/img/2.png)
之后见![image](https://github.com/llllcccjjj/qe_read/blob/main/img/3.png)长按复制下来
最终的得到的格式为![image](https://github.com/llllcccjjj/qe_read/blob/main/img/4.png)


三段之间利用@分割
###5. 填入secret COOKIE_QEYD
#### 样例：  
{"common":{"appid":1450024393,"areaid":5,"qq_ver":"8.4.10.4875","os_ver":"Android 10","mp_ver":"1.0.2","mpos_ver":"1.20.0","brand":"Xiaomi","model":"MI 8","screenWidth":393,"screenHeight":801,"windowWidth":393,"windowHeight":747,"openid":"3557920122AE63FB704655CA9F955FEF","guid":xxxxxxx,"session":"xxxxxxx","scene":3001,"source":-1,"hasRedDot":"false","missions":-1,"caseID":-1},"dataList":[{"click1":"qqauthorize_addRCS_succ_C","click2":"qqauthorize_addRCS_get_C","route":"pages/book-detail/index","refer":"pages/book-category/index","options":{"bid":"26617976"},"dis":1609900701212,"ext6":93,"eventID":"bookRead_dropOut_shelfYes_C","type":"click","bid":"26617976","ccid":1,"bookStatus":0,"bookPay":0,"chapterStatus":0,"from":"bookLib2_bookList_bookClick_C_1_26617976"}]}@https://mqqapi.reader.qq.com/mqq/样例=-1@{"ywsession":"11","Cookie":"ywguid=11;ywkey=11;platform=android;channel=mqqmina;mpVersion=0.30.0;qq_ver=8.4.18.4945;os_ver=Android 10;mpos_ver=0.30.0;platform=android;openid=11","Connection":"keep-alive","Content-Type":"application/json","Accept":"\*/\*","Host":"mqqapi.reader.qq.com","User-Agent":"1111","Referer":"https://appservice.qq.com/yangli","Accept-Language":"zh-cn","Accept-Encoding":"gzip, deflate, br","mpversion":"0.30.0"}

**⚠️cookie获取方法：**

1. 进入 https://m.q.qq.com/a/s/d3eacc70120b9a37e46bad408c0c4c2a 

2. 进一本书阅读一会儿，然后退出，获取`QQREADHEADERS` `QQREADBODYS` 和 `QQREADTIMEURL` 

3. `QQREADHEADERS` 和 `QQREADTIMEURL` 匹配链接为 https://mqqapi.reader.qq.com/mqq/addReadTimeWithBid?.......

   `QQREADBODYS` 匹配链接为 https://mqqapi.reader.qq.com/log/v4/mqq/track

4. `QQREADHEADERS`参数格式为


  ```
{"Cookie":"ywguid=123456789;ywkey=wedqwdlAWVJp9;platform=android;channel=mqqmina;mpVersion=0.30.0;qq_ver=8.4.18.4945;os_ver=Android10","aaa":"bbb",......}
  ```

多账号请按`Enter`键换行隔开示例(这里给下三个账号的示例)

  ```
{"Cookie":"ywguid=123456789;ywkey=******","aaa":"bbb",......}
{"Cookie":"ywguid=123456789;ywkey=******","aaa":"bbb",......}
{"Cookie":"ywguid=123456789;ywkey=******","aaa":"bbb",......}
  ```

5. `QQREADBODYS` 参数格式为

```
{"common":{"appid":***,"areaid":5,"qq_ver":"8.4.18.4945","os_ver":"Android 10","mp_ver":"0.31.0","mpos_ver":"1.21.0","brand":"***","model":"***","screenWidth":393,"screenHeight":816,"windowWidth":393,"windowHeight":762,"openid":"***","guid":***,"session":"***","scene":1023,"source":-1,"hasRedDot":"false","missions":-1,"caseID":-1},"dataList":[{"click1":"bookShelf_myshelf_myBook_C","click2":"qqauthorize_addRCS_succ_C","route":"pages/book-read/index","refer":"pages/book-shelf/index","options":{"bid":"27325720","cid":"3","from":"shelf"},"dis":1607325831391,"ext6":31,"eventID":"bookRead_show_I","type":"shown","ccid":3,"bid":"27325720","bookStatus":1,"bookPay":1,"chapterStatus":0,"ext1":{"font":18,"bg":0,"pageMode":1},"from":"bookShelf_myshelf_myBook_C_0_27325720"}]}
```

多账号请按`Enter`键换行隔开示例(这里给下三个账号的示例)

  ```
{"common":{"appid":***,"areaid":5,"qq_ver":"8.4.18.4945","os_ver":"Android 10","mp_ver":"0.31.0","mpos_ver":"1.21.0","brand":"***","model":"***","screenWidth":393,"screenHeight":816,"windowWidth":393,"windowHeight":762,"openid":"***","guid":***,"session":"***","scene":1023,"source":-1,"hasRedDot":"false","missions":-1,"caseID":-1},"dataList":[{"click1":"bookShelf_myshelf_myBook_C","click2":"qqauthorize_addRCS_succ_C","route":"pages/book-read/index","refer":"pages/book-shelf/index","options":{"bid":"27325720","cid":"3","from":"shelf"},"dis":1607325831391,"ext6":31,"eventID":"bookRead_show_I","type":"shown","ccid":3,"bid":"27325720","bookStatus":1,"bookPay":1,"chapterStatus":0,"ext1":{"font":18,"bg":0,"pageMode":1},"from":"bookShelf_myshelf_myBook_C_0_27325720"}]}
{"common":{"appid":***,"areaid":5,"qq_ver":"8.4.18.4945","os_ver":"Android 10","mp_ver":"0.31.0","mpos_ver":"1.21.0","brand":"***","model":"***","screenWidth":393,"screenHeight":816,"windowWidth":393,"windowHeight":762,"openid":"***","guid":***,"session":"***","scene":1023,"source":-1,"hasRedDot":"false","missions":-1,"caseID":-1},"dataList":[{"click1":"bookShelf_myshelf_myBook_C","click2":"qqauthorize_addRCS_succ_C","route":"pages/book-read/index","refer":"pages/book-shelf/index","options":{"bid":"27325720","cid":"3","from":"shelf"},"dis":1607325831391,"ext6":31,"eventID":"bookRead_show_I","type":"shown","ccid":3,"bid":"27325720","bookStatus":1,"bookPay":1,"chapterStatus":0,"ext1":{"font":18,"bg":0,"pageMode":1},"from":"bookShelf_myshelf_myBook_C_0_27325720"}]}
{"common":{"appid":***,"areaid":5,"qq_ver":"8.4.18.4945","os_ver":"Android 10","mp_ver":"0.31.0","mpos_ver":"1.21.0","brand":"***","model":"***","screenWidth":393,"screenHeight":816,"windowWidth":393,"windowHeight":762,"openid":"***","guid":***,"session":"***","scene":1023,"source":-1,"hasRedDot":"false","missions":-1,"caseID":-1},"dataList":[{"click1":"bookShelf_myshelf_myBook_C","click2":"qqauthorize_addRCS_succ_C","route":"pages/book-read/index","refer":"pages/book-shelf/index","options":{"bid":"27325720","cid":"3","from":"shelf"},"dis":1607325831391,"ext6":31,"eventID":"bookRead_show_I","type":"shown","ccid":3,"bid":"27325720","bookStatus":1,"bookPay":1,"chapterStatus":0,"ext1":{"font":18,"bg":0,"pageMode":1},"from":"bookShelf_myshelf_myBook_C_0_27325720"}]}
  ```

6. `QQREADTIMEURL` 参数格式为

```
https://mqqapi.reader.qq.com/mqq/addReadTimeWithBid?scene=***&refer=-1&bid=***&readTime=***&read_type=0&conttype=1&read_status=0&chapter_info=%5B%7B%221%22%3A%7B%22readTime%22%3A***%2C%22pay_status%22%3A0%7D%7D%5D&sp=-1
```

多账号请按`Enter`键换行隔开示例(这里给下三个账号的示例)

  ```
https://mqqapi.reader.qq.com/mqq/addReadTimeWithBid?scene=***&refer=-1&bid=***&readTime=***&read_type=0&conttype=1&read_status=0&chapter_info=%5B%7B%221%22%3A%7B%22readTime%22%3A***%2C%22pay_status%22%3A0%7D%7D%5D&sp=-1
https://mqqapi.reader.qq.com/mqq/addReadTimeWithBid?scene=***&refer=-1&bid=***&readTime=***&read_type=0&conttype=1&read_status=0&chapter_info=%5B%7B%221%22%3A%7B%22readTime%22%3A***%2C%22pay_status%22%3A0%7D%7D%5D&sp=-1
https://mqqapi.reader.qq.com/mqq/addReadTimeWithBid?scene=***&refer=-1&bid=***&readTime=***&read_type=0&conttype=1&read_status=0&chapter_info=%5B%7B%221%22%3A%7B%22readTime%22%3A***%2C%22pay_status%22%3A0%7D%7D%5D&sp=-1
