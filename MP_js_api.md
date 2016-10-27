[相关官方文档](http://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1421141115&token=&lang=zh_CN)

WxMpService提供了以下几个方法：

```java
public String getJsapiTicket() throws WxErrorException;

public String getJsapiTicket(boolean forceRefresh) throws WxErrorException;

public WxMpJsapiSignature createJsapiSignature(String url) throws WxErrorException;
```
