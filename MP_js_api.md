[相关官方文档](http://mp.weixin.qq.com/wiki/7/aaa137b55fb2e0456bf8dd9148dd613f.html#.E9.99.84.E5.BD.951-JS-SDK.E4.BD.BF.E7.94.A8.E6.9D.83.E9.99.90.E7.AD.BE.E5.90.8D.E7.AE.97.E6.B3.95)

WxMpService提供了以下几个方法：

```java
public String getJsapiTicket() throws WxErrorException;

public String getJsapiTicket(boolean forceRefresh) throws WxErrorException;

public String createJsapiSignature(long timestamp, String noncestr, String url) throws WxErrorException;
```
