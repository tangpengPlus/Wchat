```java
WxMpTemplateMessage templateMessage = new WxMpTemplateMessage();
templateMessage.setToUser(...);
templateMessage.setTemplateId(...);
templateMessage.setUrl(...);
templateMessage.getData().add(new WxMpTemplateData(name1, value1, color2));
templateMessage.getData().add(new WxMpTemplateData(name2, value2, color2));

wxMpService.getTemplateMsgService().sendTemplateMsg(templateMessage);
```
更详细的使用方法请参考单元测试代码：
`/weixin-java-mp/src/test/java/me/chanjar/weixin/mp/api/impl/WxMpTemplateMsgServiceImplTest.java`