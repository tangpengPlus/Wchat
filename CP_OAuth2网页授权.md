## 构造网页授权url

首先构造网页授权url，然后构成超链接让用户点击

```java
wxCpService.oauth2buildAuthorizationUrl(null)
```

## 获得用户基本信息

当用户同意授权后，会回调所设置的url并把authorization code传过来，然后用这个code获得user id

```java
String[] res = wxCpService.oauth2getUserInfo(code);
String userId = res[0];
String deviceId = res[1];
```
