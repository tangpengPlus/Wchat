下面用用户列表群发（``WxMpMassOpenIdsMessage``）做例子，如果要使用分组群发，则使用``WxMpMassGroupMessage``即可。

## 文本消息
```java
WxMpMassOpenIdsMessage massMessage = new WxMpMassOpenIdsMessage();
massMessage.setMsgType(WxConsts.MASS_MSG_TEXT);
massMessage.setContent("消息内容");
massMessage.getToUsers().add(openid);

WxMpMassSendResult massResult = wxMpService.massOpenIdsMessageSend(massMessage);
```

## 视频消息
```java
WxMediaUploadResult uploadMediaRes = wxMpService.mediaUpload(WxConsts.MEDIA_VIDEO, WxConsts.FILE_MP4, inputStream);

// 把视频变成可被群发的媒体
WxMpMassVideo video = new WxMpMassVideo();
video.setTitle("测试标题");
video.setDescription("测试描述");
video.setMediaId(uploadMediaRes.getMediaId());
WxMpMassUploadResult uploadResult = wxMpService.massVideoUpload(video);

WxMpMassOpenIdsMessage massMessage = new WxMpMassOpenIdsMessage();
massMessage.setMsgType(WxConsts.MASS_MSG_VIDEO);
massMessage.setMediaId(uploadResult.getMediaId());
massMessage.getToUsers().add(openid);

WxMpMassSendResult massResult = wxMpService.massOpenIdsMessageSend(massMessage);
```

## 图片消息
```java
WxMediaUploadResult uploadMediaRes = wxMpService.mediaUpload(WxConsts.MEDIA_IMAGE, WxConsts.FILE_JPG, inputStream);

WxMpMassOpenIdsMessage massMessage = new WxMpMassOpenIdsMessage();
massMessage.setMsgType(WxConsts.MASS_MSG_IMAGE);
massMessage.setMediaId(uploadMediaRes.getMediaId());
massMessage.getToUsers().add(openid);

WxMpMassSendResult massResult = wxMpService.massOpenIdsMessageSend(massMessage);
```

## 语音消息
```java
WxMediaUploadResult uploadMediaRes = wxMpService.mediaUpload(WxConsts.MEDIA_VOICE, WxConsts.FILE_MP3, inputStream);

WxMpMassOpenIdsMessage massMessage = new WxMpMassOpenIdsMessage();
massMessage.setMsgType(WxConsts.MASS_MSG_VOICE);
massMessage.setMediaId(uploadMediaRes.getMediaId());
massMessage.getToUsers().add(openid);

WxMpMassSendResult massResult = wxMpService.massOpenIdsMessageSend(massMessage);
```

## 图文消息
```java
// 先上传图文消息里需要的图片
WxMediaUploadResult uploadResult = wxMpService.mediaUpload(WxConsts.MEDIA_IMAGE, WxConsts.FILE_JPG, inputStream);

WxMpMassNews news = new WxMpMassNews();
WxMpMassNews.WxMpMassNewsArticle article1 = new WxMpMassNews.WxMpMassNewsArticle();
article1.setTitle("标题1");
article1.setContent("内容1");
article1.setThumbMediaId(uploadMediaRes.getMediaId());
news.addArticle(article1);

WxMpMassNews.WxMpMassNewsArticle article2 = new WxMpMassNews.WxMpMassNewsArticle();
article2.setTitle("标题2");
article2.setContent("内容2");
article2.setThumbMediaId(uploadMediaRes.getMediaId());
article2.setShowCoverPic(true);
article2.setAuthor("作者2");
article2.setContentSourceUrl("www.baidu.com");
article2.setDigest("摘要2");
news.addArticle(article2);

WxMpMassUploadResult massUploadResult = wxMpService.massNewsUpload(news);

WxMpMassOpenIdsMessage massMessage = new WxMpMassOpenIdsMessage();
massMessage.setMsgType(WxConsts.MASS_MSG_NEWS);
massMessage.setMediaId(uploadResult.getMediaId());
massMessage.getToUsers().add(openid);

WxMpMassSendResult massResult = wxMpService.massOpenIdsMessageSend(massMessage);
```
