微信公众平台对推送给服务器的消息提供了加密机制，开发人员在微信公众号管理界面选择是是否启用。

需要注意的是，根据微信官方文档，如果微信传过来的是加密信息，那么返回给微信的也得是加密信息。

下面是``WxMpDemoServlet``中对加解密的处理。

```java
@Override protected void service(HttpServletRequest request, HttpServletResponse response)
    throws ServletException, IOException {

  String signature = request.getParameter("signature");
  String nonce = request.getParameter("nonce");
  String timestamp = request.getParameter("timestamp");

  response.setContentType("text/html;charset=utf-8");
  response.setStatus(HttpServletResponse.SC_OK);

  if (!wxMpService.checkSignature(timestamp, nonce, signature)) {
    // 消息签名不正确，说明不是公众平台发过来的消息
    response.getWriter().println("非法请求");
    return;
  }

  String echostr = request.getParameter("echostr");
  if (StringUtils.isNotBlank(echostr)) {
    // 说明是一个仅仅用来验证的请求，回显echostr
    response.getWriter().println(echostr);
    return;
  }

  String encryptType = StringUtils.isBlank(request.getParameter("encrypt_type")) ?
      "raw" :
      request.getParameter("encrypt_type");

  WxMpXmlMessage inMessage = null;

  if ("raw".equals(encryptType)) {
    // 明文传输的消息
    inMessage = WxMpXmlMessage.fromXml(request.getInputStream());
  } else if ("aes".equals(encryptType)) {
    // 是aes加密的消息
    String msgSignature = request.getParameter("msg_signature");
    inMessage = WxMpXmlMessage.fromEncryptedXml(request.getInputStream(), wxMpConfigStorage, timestamp, nonce, msgSignature);
  } else {
    response.getWriter().println("不可识别的加密类型");
    return;
  }

  WxMpXmlOutMessage outMessage = wxMpMessageRouter.route(inMessage);

  if (outMessage != null) {
    if ("raw".equals(encryptType)) {
      response.getWriter().write(outMessage.toXml());
    } else if ("aes".equals(encryptType)) {
      response.getWriter().write(outMessage.toEncryptedXml(wxMpConfigStorage));
    }
    return;
  }

}
```

## 加解密构成中的异常

如果在加解密的过程中出现``java.security.InvalidKeyException: Illegal key size``，则需要下载一个东西：

 * JRE/JDK 6：http://www.oracle.com/technetwork/java/javase/downloads/jce-6-download-429243.html
 * JRE/JDK 7：http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html
 * JRE/JDK 8：http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html

如果安装了JRE，将两个jar文件放到``$JAVA_HOME/lib/security``目录下覆盖原来的文件

如果安装了JDK，将两个jar文件放到``$JAVA_HOME/jre/lib/security``目录下覆盖原来文件
