## 更新用户备注名
```java
wxMpService.userUpdateRemark(openid, "测试备注名");
```

## 获得用户信息
```java
String lang = "zh_CN"; //语言
WxMpUser user = wxMpService.getUserService().userInfo(openid,lang);
```

## 获得用户列表
```java
WxMpUserList wxUserList = wxMpService.userList(next_openid);
```

## 查询用户所在分组
```java
long groupid = wxMpService.userGetGroup(openid);
```

## 将用户移到分组
```java
wxMpService.userUpdateGroup(openid, to_groupid);
```
