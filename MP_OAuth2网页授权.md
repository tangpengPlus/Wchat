## 构造网页授权url

首先构造网页授权url，然后构成超链接让用户点击

```java
String url = ...;
wxMpService.oauth2buildAuthorizationUrl(url, WxConsts.OAUTH2_SCOPE_USER_INFO, null)
```

## 获得access token

当用户同意授权后，会回调所设置的url并把authorization code传过来，然后用这个code获得access token

```java
WxMpOAuth2AccessToken wxMpOAuth2AccessToken = wxMpService.oauth2getAccessToken(code);
```

## 获得用户基本信息

```java
WxMpUser wxMpUser = wxMpService.oauth2getUserInfo(wxMpOAuth2AccessToken, null);
```

## 刷新access token

```java
wxMpOAuth2AccessToken = wxMpService.oauth2refreshAccessToken(wxMpOAuth2AccessToken.getRefreshToken());
```

## 验证access token

```java
boolean valid = wxMpService.oauth2validateAccessToken(wxMpOAuth2AccessToken);
```
