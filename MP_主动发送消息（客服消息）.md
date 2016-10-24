```java
WxMpCustomMessage message = ...;
// 设置消息的内容等信息
wxMpService.getKefuService().customMessageSend(message);
```

## WxXmlOutTextMessage

不同类型的客服消息有不同的构造方法：

### 文本消息

```java
WxMpCustomMessage
  .TEXT()
  .toUser("OPENID")
  .content("sfsfdsdf")
  .build();
```
### 图片消息
```java
WxMpCustomMessage
  .IMAGE()
  .toUser("OPENID")
  .mediaId("MEDIA_ID")
  .build();
```

### 语音消息
```java
WxMpCustomMessage.VOICE()
  .toUser("OPENID")
  .mediaId("MEDIA_ID")
  .build();
```

### 视频消息
```java
WxMpCustomMessage.VIDEO()
  .toUser("OPENID")
  .title("TITLE")
  .mediaId("MEDIA_ID")
  .thumbMediaId("MEDIA_ID")
  .description("DESCRIPTION")
  .build();
```

### 音乐消息
```java
WxMpCustomMessage.MUSIC()
  .toUser("OPENID")
  .title("TITLE")
  .thumbMediaId("MEDIA_ID")
  .description("DESCRIPTION")
  .musicUrl("MUSIC_URL")
  .hqMusicUrl("HQ_MUSIC_URL")
  .build();
```

### 图文消息
```java
WxMpCustomMessage.WxArticle article1 = new WxMpCustomMessage.WxArticle();
article1.setUrl("URL");
article1.setPicUrl("PIC_URL");
article1.setDescription("Is Really A Happy Day");
article1.setTitle("Happy Day");

WxMpCustomMessage.WxArticle article2 = new WxMpCustomMessage.WxArticle();
article2.setUrl("URL");
article2.setPicUrl("PIC_URL");
article2.setDescription("Is Really A Happy Day");
article2.setTitle("Happy Day");

WxMpCustomMessage.NEWS()
    .toUser("OPENID")
    .addArticle(article1)
    .addArticle(article2)
    .build();
```
