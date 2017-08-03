## 移动家庭能力开放平台 Authorization 生成器
>最近在研究这个平台，愁于没有自动生成工具，不便于测试，于是写了个生成器

### 1.官方的加密流程
 - 1、 MD5编码apiKey+secretKey+time所拼接的字符串，亦即signStr= MD5(${apiKey} + ${secretKey} +${ time})；
 - 2、 将MD5编码之后的字符串和apiKey，time一并处理为JSON字符串，亦即
 ```
jsonStr = {
"apiKey": "b03596215489417089131859ca769718",
"time": "1459217778516",
"sign": "${signStr}"
}
```

 - 3、 将JSON串进行Base64编码然后填充到头部，Authorization=Base64(jsonStr)
其中time为时间戳。Base64的作用是将json字符串编码，采用的apache.commons.codec提供的编码方法（建议采用该包做base64处理）。

## 生成器使用到的工具
>基于javascript

 - md5.js(项目里有)
 - [jbase64.js](https://git.oschina.net/loonhxl/jbase64.git)


### 日志

 - 2017.8.2 基本架构
 - 2017.8.3 进行功能优化