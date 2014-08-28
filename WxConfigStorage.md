``WxConfigStorage`` 是存储和管理微信公众号相关信息的地方，里面有：

1. appid
1. app secret
1. access token
1. token 

这些信息。

在[Quickstart](https://github.com/chanjarster/weixin-java-tools/wiki/Quickstart)的例子里我们使用的是``WxInMemoryConfigStorage``。在正式生产环境中，你可以提供自己的实现，比如在集群环境下将这些信息存储到数据库里，以便各个节点能够共享access token。