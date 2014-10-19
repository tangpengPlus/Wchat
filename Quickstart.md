在你的maven项目中添加：
```xml
<dependency>
  <groupId>me.chanjar</groupId>
  <artifactId>weixin-java-tools</artifactId>
  <version>1.0.0</version>
</dependency>
```

## Hello World
```java
WxInMemoryConfigStorage config = new WxInMemoryConfigStorage();
config.setAppId(...); // 设置微信公众号的appid
config.setSecret(...); // 设置微信公众号的app secret
config.setToken(...); // 设置微信公众号的token

WxServiceImpl wxService = new WxServiceImpl();
wxService.setWxConfigStorage(config);

// 用户的openid在下面地址获得 
// https://mp.weixin.qq.com/debug/cgi-bin/apiinfo?t=index&type=用户管理&form=获取关注者列表接口%20/user/get 
String openid = ...; 
WxCustomMessage message = WxCustomMessage.TEXT().toUser(openid).content("Hello World").build();
wxService.customMessageSend(message);
```