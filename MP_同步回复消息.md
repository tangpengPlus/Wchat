``WxMessageRouter``默认使用异步的方式处理消息，如果要使用同步回复微信消息，那么:

1. 需要将路由规则配置为同步
2. 且handler需要返回一个``WxMpXmlOutMessage``

```java
// 将WxXmlMessage交给消息路由器
HttpServletRequest request = ...;
WxXmlMessage inMsg = ...;
WxMpXmlOutMessage reMsg = router.route(inMsg);
if (reMsg != null) {
  // 说明是同步回复的消息
  // 将xml写入HttpServletResponse
  response.getWriter().write(reMsg.toXml());
} else {
  // 说明是异步回复的消息，直接将空字符串写入HttpServletResponse
}
```

## WxMpXmlOutTextMessage

``WxMpXmlOutTextMessage``是同步回复给微信消息的对象，不同类型的消息类型可以用不同的方式构造：

### 文本消息

```java
WxMpXmlOutMessage.TEXT()
  .content("content")
  .fromUser("from")
  .toUser("to")
  .build();
```

### 图片消息

```java
WxMpXmlOutMessage.IMAGE()
  .mediaId("ddfefesfsdfef")
  .fromUser("from")
  .toUser("to")
  .build();
```

### 语音消息

```java
WxMpXmlOutMessage.VOICE()
  .mediaId("ddfefesfsdfef")
  .fromUser("from")
  .toUser("to")
  .build();
```

### 视频消息

```java
WxMpXmlOutMessage.VIDEO()
  .mediaId("media_id")
  .fromUser("fromUser")
  .toUser("toUser")
  .title("title")
  .description("ddfff")
  .build();
```
### 音乐消息
```java
WxMpXmlOutMessage.MUSIC()
  .fromUser("fromUser")
  .toUser("toUser")
  .title("title")
  .description("ddfff")
  .hqMusicUrl("hQMusicUrl")
  .musicUrl("musicUrl")
  .thumbMediaId("thumbMediaId")
  .build();
```
### 图文消息

```java
WxMpXmlOutNewsMessage.Item item = new WxMpXmlOutNewsMessage.Item();
item.setDescription("description");
item.setPicUrl("picUrl");
item.setTitle("title");
item.setUrl("url");

WxMpXmlOutNewsMessage m = WxMpXmlOutMessage.NEWS()
  .fromUser("fromUser")
  .toUser("toUser")
  .addArticle(item)
  .build();
```
