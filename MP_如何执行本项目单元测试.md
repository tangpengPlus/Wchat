如果你需要执行本项目的单元测试代码，那么你需要将 ``src/test/resources/test-config.sample.xml`` 改成 ``test-config.xml`` ，并填写以下信息：

```xml
<xml>
    <appId>公众号appID</appId>
    <secret>公众号appsecret</secret>
    <token>公众号Token</token>
    <aesKey>公众号EncodingAESKey</aesKey>
    <accessToken>可以不填写</accessToken>
    <expiresTime>可以不填写</expiresTime>
    <openId>某个加你公众号的用户的openId</openId>
</xml>
```

```bash
mvn clean test
```

要注意的是，如果使用开发者测试账号执行单元测试话，会在短链接的测试部分失败，这是因为测试账号没有开放这个接口。

如果一天测试多次的话，群发接口的测试部分也会失败，因为超出了每天接口调用上限（4次）。
