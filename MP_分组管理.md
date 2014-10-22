## 创建分组
```java
WxGroup res = wxMpService.groupCreate("测试分组1");
```

## 获得分组列表
```java
List<WxGroup> groupList = wxMpService.groupGet();
```

## 更新分组名
```java
WxMpGroup group = new WxMpGroup();
group.setId(...);
group.setName(...);
wxMpService.groupUpdate(group);
```
