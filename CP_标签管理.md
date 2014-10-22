## 新建标签

要注意的是，通过API新建的标签默认处于解锁状态，要到管理员界面里把标签锁定，然后再刷新管理员界面，才能够在管理员界面删除标签

```java
tagId = wxService.tagCreate("测试标签4");
```

## 更新标签

```java
wxService.tagUpdate(tagId, "测试标签-改名");
```

## 获得标签

```java
List<WxCpTag> tags = wxService.tagGet();
```

## 将用户添加到标签

```java
List<String> userIds = new ArrayList<String>();
userIds.add(userId);
wxService.tagAddUsers(tagId, userIds);
```

## 获取某标签下用户

```java
List<WxCpUser> users = wxService.tagGetUsers(tagId);
```

## 将用户从标签中移除

```java
List<String> userIds = new ArrayList<String>();
userIds.add(userId);
wxService.tagRemoveUsers(tagId, userIds);
```

## 删除标签

```java
wxService.tagDelete(tagId);
```
