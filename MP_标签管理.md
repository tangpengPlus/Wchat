## 创建标签
```java
WxGroup res = wxMpService.groupCreate("测试分组1");
```

## 获得标签列表
```java
List<WxGroup> groupList = wxMpService.groupGet();
```

## 更新标签名
```java
WxMpGroup group = new WxMpGroup();
group.setId(...);
group.setName(...);
wxMpService.groupUpdate(group);
```
