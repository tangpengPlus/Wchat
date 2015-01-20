## Hello World
```java
WxCpInMemoryConfigStorage config = new WxCpInMemoryConfigStorage();
config.setCorpId("...");      // 设置微信企业号的appid
config.setCorpSecret("...");  // 设置微信企业号的app corpSecret
config.setAgentId("...");     // 设置微信企业号应用ID
config.setToken("...");       // 设置微信企业号应用的token
config.setAesKey("...");      // 设置微信企业号应用的EncodingAESKey

WxCpServiceImpl wxCpService = new WxCpServiceImpl();
wxCpService.setWxCpConfigStorage(config);

String userId = "...";
WxCpMessage message = WxCpMessage.TEXT().agentId("...").toUser(userId).content("Hello World").build();
wxCpService.messageSend(message);
```

## Servlet Example
```java
public class WxCpServlet extends HttpServlet {

  protected WxCpConfigStorage wxCpConfigStorage;
  protected WxCpService wxCpService;
  protected WxCpMessageRouter wxCpMessageRouter;

  @Override public void init() throws ServletException {
    super.init();

    wxCpConfigStorage = new WxCpInMemoryConfigStorage();
    config.setCorpId("...");      // 设置微信企业号的appid
    config.setCorpSecret("...");  // 设置微信企业号的app corpSecret
    config.setAgentId("...");     // 设置微信企业号应用ID
    config.setToken("...");       // 设置微信企业号应用的token
    config.setAesKey("...");      // 设置微信企业号应用的EncodingAESKey

    wxCpService = new WxCpServiceImpl();
    wxCpService.setWxCpConfigStorage(wxCpConfigStorage);

    WxCpMessageHandler handler = new WxCpMessageHandler() {
      @Override public WxCpXmlOutMessage handle(WxCpXmlMessage wxMessage, Map<String, Object> context, WxCpService wxCpService) {
        WxCpXmlOutTextMessage m = WxCpXmlOutMessage
                .TEXT()
                .content("测试加密消息")
                .fromUser(wxMessage.getToUserName())
                .toUser(wxMessage.getFromUserName())
            .build();
        return m;
      }
    };

    wxCpMessageRouter = new WxCpMessageRouter(wxCpService);
    wxCpMessageRouter
        .rule()
        .async(false)
        .content("哈哈") // 拦截内容为“哈哈”的消息
        .handler(handler)
        .end();
  }

  @Override protected void service(HttpServletRequest request, HttpServletResponse response)
      throws ServletException, IOException {

    response.setContentType("text/html;charset=utf-8");
    response.setStatus(HttpServletResponse.SC_OK);

    String msgSignature = request.getParameter("msg_signature");
    String nonce = request.getParameter("nonce");
    String timestamp = request.getParameter("timestamp");
    String echostr = request.getParameter("echostr");

    if (StringUtils.isNotBlank(echostr)) {
      if (!wxCpService.checkSignature(msgSignature, timestamp, nonce, echostr)) {
        // 消息签名不正确，说明不是公众平台发过来的消息
        response.getWriter().println("非法请求");
        return;
      }
      WxCpCryptUtil cryptUtil = new WxCpCryptUtil(wxCpConfigStorage);
      String plainText = cryptUtil.decrypt(echostr);
      // 说明是一个仅仅用来验证的请求，回显echostr
      response.getWriter().println(plainText);
      return;
    }

    WxCpXmlMessage inMessage = WxCpXmlMessage.fromEncryptedXml(request.getInputStream(), wxCpConfigStorage, timestamp, nonce, msgSignature);
    WxCpXmlOutMessage outMessage = wxCpMessageRouter.route(inMessage);
    if (outMessage != null) {
      response.getWriter().write(outMessage.toEncryptedXml(wxCpConfigStorage));
    }

    return;
  }

}
```
