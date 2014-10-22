微信企业号支持对用户身份做第二次验证，验证的方式就是将用户跳转到企业的页面，验证成功后企业应用需告诉企业号验证成功。

```java
wxCpService.userAuthenticated(userId);
```
