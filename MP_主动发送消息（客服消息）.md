```java
WxMpKefuMessage message = ...;
// 设置消息的内容等信息
wxMpService.getKefuService().sendKefuMessage(message);
```

## WxXmlOutTextMessage

不同类型的客服消息有不同的构造方法：

### 文本消息

```java
WxMpKefuMessage
  .TEXT()
  .toUser("OPENID")
  .content("sfsfdsdf")
  .build();
```
### 图片消息
```java
WxMpKefuMessage
  .IMAGE()
  .toUser("OPENID")
  .mediaId("MEDIA_ID")
  .build();
```

### 语音消息
```java
WxMpKefuMessage.VOICE()
  .toUser("OPENID")
  .mediaId("MEDIA_ID")
  .build();
```

### 视频消息
```java
WxMpKefuMessage.VIDEO()
  .toUser("OPENID")
  .title("TITLE")
  .mediaId("MEDIA_ID")
  .thumbMediaId("MEDIA_ID")
  .description("DESCRIPTION")
  .build();
```

### 音乐消息
```java
WxMpKefuMessage.MUSIC()
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
WxMpKefuMessage.WxArticle article1 = new WxMpKefuMessage.WxArticle();
article1.setUrl("URL");
article1.setPicUrl("PIC_URL");
article1.setDescription("Is Really A Happy Day");
article1.setTitle("Happy Day");

WxMpKefuMessage.WxArticle article2 = new WxMpKefuMessage.WxArticle();
article2.setUrl("URL");
article2.setPicUrl("PIC_URL");
article2.setDescription("Is Really A Happy Day");
article2.setTitle("Happy Day");

WxMpKefuMessage.NEWS()
    .toUser("OPENID")
    .addArticle(article1)
    .addArticle(article2)
    .build();
```
