在你的maven项目中添加：

```xml
<dependency>
  <groupId>me.chanjar</groupId>
  <artifactId>weixin-java-mp</artifactId>
  <version>1.0.3</version>
</dependency>
```

如果要使用``*-SNAPSHOT``版，则需要在你的``pom.xml``中添加这段：

```xml
<repositories>
  <repository>
      <snapshots />
      <id>sonatype snapshots</id>
      <url>https://oss.sonatype.org/content/repositories/snapshots/</url>
  </repository>
</repositories>
```

## Hello World
```java
WxMpInMemoryConfigStorage config = new WxMpInMemoryConfigStorage();
config.setAppId("..."); // 设置微信公众号的appid
config.setSecret("..."); // 设置微信公众号的app corpSecret
config.setToken("..."); // 设置微信公众号的token
config.setAesKey("..."); // 设置微信公众号的EncodingAESKey

WxMpServiceImpl wxService = new WxMpServiceImpl();
wxService.setWxMpConfigStorage(config);

// 用户的openid在下面地址获得 
// https://mp.weixin.qq.com/debug/cgi-bin/apiinfo?t=index&type=用户管理&form=获取关注者列表接口%20/user/get 
String openid = "...";
WxMpCustomMessage message = WxMpCustomMessage.TEXT().toUser(openid).content("Hello World").build();
wxService.customMessageSend(message);
```
