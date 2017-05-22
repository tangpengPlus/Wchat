和公众号不同，企业号消息发送接口本身就带有群发功能。

```java
WxCpMessage message = ...;
// 设置消息的内容等信息
wxCpService.messageSend(message);
```

## WxXmlOutTextMessage

不同类型的客服消息有不同的构造方法：

### 文本消息

```java
WxCpMessage
  .TEXT()
  .agentId(...) // 企业号应用ID
  .toUser("非必填，UserID列表（消息接收者，多个接收者用‘|’分隔）。特殊情况：指定为@all，则向关注该企业应用的全部成员发送")
  .toParty("非必填，PartyID列表，多个接受者用‘|’分隔。当touser为@all时忽略本参数")
  .toTag("非必填，TagID列表，多个接受者用‘|’分隔。当touser为@all时忽略本参数")
  .content("sfsfdsdf")
  .build();
```
### 图片消息
```java
WxCpMessage
  .IMAGE()
  .agentId(...) // 企业号应用ID
  .toUser("非必填，UserID列表（消息接收者，多个接收者用‘|’分隔）。特殊情况：指定为@all，则向关注该企业应用的全部成员发送")
  .toParty("非必填，PartyID列表，多个接受者用‘|’分隔。当touser为@all时忽略本参数")
  .toTag("非必填，TagID列表，多个接受者用‘|’分隔。当touser为@all时忽略本参数")
  .mediaId("MEDIA_ID")
  .build();
```

### 语音消息
```java
WxCpMessage.VOICE()
  .agentId(...) // 企业号应用ID
  .toUser("非必填，UserID列表（消息接收者，多个接收者用‘|’分隔）。特殊情况：指定为@all，则向关注该企业应用的全部成员发送")
  .toParty("非必填，PartyID列表，多个接受者用‘|’分隔。当touser为@all时忽略本参数")
  .toTag("非必填，TagID列表，多个接受者用‘|’分隔。当touser为@all时忽略本参数")
  .mediaId("MEDIA_ID")
  .build();
```

### 视频消息
```java
WxCpMessage.VIDEO()
  .agentId(...) // 企业号应用ID
  .toUser("非必填，UserID列表（消息接收者，多个接收者用‘|’分隔）。特殊情况：指定为@all，则向关注该企业应用的全部成员发送")
  .toParty("非必填，PartyID列表，多个接受者用‘|’分隔。当touser为@all时忽略本参数")
  .toTag("非必填，TagID列表，多个接受者用‘|’分隔。当touser为@all时忽略本参数")
  .title("TITLE")
  .mediaId("MEDIA_ID")
  .thumbMediaId("MEDIA_ID")
  .description("DESCRIPTION")
  .build();
```

### 图文消息
```java
NewArticle article1 = new NewArticle();
article1.setUrl("URL");
article1.setPicUrl("PIC_URL");
article1.setDescription("Is Really A Happy Day");
article1.setTitle("Happy Day");

NewArticle article2 = new NewArticle();
article2.setUrl("URL");
article2.setPicUrl("PIC_URL");
article2.setDescription("Is Really A Happy Day");
article2.setTitle("Happy Day");

WxCpMessage.NEWS()
  .agentId(...) // 企业号应用ID
  .toUser("非必填，UserID列表（消息接收者，多个接收者用‘|’分隔）。特殊情况：指定为@all，则向关注该企业应用的全部成员发送")
  .toParty("非必填，PartyID列表，多个接受者用‘|’分隔。当touser为@all时忽略本参数")
  .toTag("非必填，TagID列表，多个接受者用‘|’分隔。当touser为@all时忽略本参数")
  .addArticle(article1)
  .addArticle(article2)
  .build();
```
