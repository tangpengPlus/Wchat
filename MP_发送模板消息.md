```java
WxMpTemplateMessage templateMessage = new WxMpTemplateMessage();
templateMessage.setToUser(...);
templateMessage.setTemplateId(...);
templateMessage.setUrl(...);
templateMessage.setTopColor(...);
templateMessage.getDatas().add(new WxMpTemplateData(name1, value1, color2));
templateMessage.getDatas().add(new WxMpTemplateData(name2, value2, color2));

wxMpService.getTemplateMsgService().sendTemplateMsg(templateMessage);
```