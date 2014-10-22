如果你需要执行本项目的单元测试代码，那么你需要将 ``src/test/resources/test-config.sample.xml`` 改成 ``test-config.xml`` ，并填写以下信息：

```xml
<xml>
    <corpId>企业号corpid</corpId>
    <corpSecret>企业号corpsecret</corpSecret>
    <agentId>企业号应用id</agentId>
    <token>企业号应用Token</token>
    <aesKey>企业号应用EncodingAESKey</aesKey>
    <accessToken>可以不填写</accessToken>
    <expiresIn>可以不填写</expiresIn>
    <userId>企业号通讯录里的某个userid</userId>
    <departmentId>企业号通讯录的某个部门id</departmentId>
    <tagId>企业号通讯录里的某个tagid</tagId>
</xml>
```

```bash
mvn clean test
```
