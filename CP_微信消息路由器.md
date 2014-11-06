微信推送给公众号的消息类型很多，而公众号也需要针对用户不同的输入做出不同的反应。

如果使用``if ... else ...``来实现的话非常难以维护，这时可以使用``WxMessageRouter``来对消息进行路由。

``WxMessageRouter``支持从4个角度对消息进行匹配，然后交给事先指定的``WxMessageHandler``：

1. agentId
1. msgType
1. event
1. eventKey
1. content

**在整个应用程序中，``WxMessageRouter``应该是单例的。**

```java
WxCpMessageRouter router = new WxCpMessageRouter();
router
    // 4个条件必须全部匹配的路由规则
    .rule()
      .agentId(1)
      .handler(hander)
    .end()
    .rule()
      .msgType(WxConsts.XML_MSG_TEXT)
      .event(WxConsts.EVT_SUBSCRIBE)
      .eventKey("EVENT_KEY")
      .content("CONTENT")
      .rContent("content正则表达式")
      .handler(handler)
    .end()
        // 只匹配1个条件的路由规则
    .rule()
      .msgType("MSG_TYPE")
      .handler(handler)
    .end()
        // 消息经过这个规则后可以继续尝试后面的路由规则
    .rule()
      .msgType("MSG_TYPE")
      .handler(handler)
    .next()
        // 另一个同步处理的路由规则
    .rule()
      .async(false)
      .msgType("MSG_TYPE")
      .handler(handler)
    .end()
        // 添加了拦截器的路由规则
    .rule()
      .msgType("MSG_TYPE")
      .interceptor(interceptor)
      .handler(handler)
    .end()
        // 兜底路由规则，一般放到最后
    .rule()
      .handler(handler)
    .end()
;

// 将WxXmlMessage交给消息路由器
HttpServletRequest request =...;
WxCpXmlMessage message =...;
router.route(message);
```

1. 配置路由规则时要按照从细到粗的原则，否则可能消息可能会被提前处理
2. 规则的结束必须用``Rule.end()``或者``Rule.next()``，否则不会生效
3. 具体使用可以看源代码中的``WxCpMessageRouterTest``单元测试，或者查看Javadoc

关于如何构造``WxCpXmlMessage``请看[同步回复消息](https://github.com/chanjarster/weixin-java-tools/wiki/CP_同步回复消息)。


## WxMessageHandler

```java
public interface WxCpMessageHandler {

  /**
   *
   * @param wxMessage
   * @param context  上下文，如果handler或interceptor之间有信息要传递，可以用这个
   * @return xml格式的消息，如果在异步规则里处理的话，可以返回null
   */
  public WxCpXmlOutMessage handle(WxCpXmlMessage wxMessage, Map<String, Object> context);

}
```

## WxMessageInterceptor

```java
public interface WxCpMessageInterceptor {

  /**
   * 拦截微信消息
   * @param wxMessage
   * @param context  上下文，如果handler或interceptor之间有信息要传递，可以用这个
   * @return  true代表OK，false代表不OK
   */
  public boolean intercept(WxCpXmlMessage wxMessage, Map<String, Object> context);

}
```