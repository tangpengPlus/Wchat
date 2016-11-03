更多使用用例可参考单元测试类me.chanjar.weixin.mp.api.impl.WxMpUserTagServiceImplTest

## 创建标签
```java
WxUserTag res = this.wxService.getUserTagService().tagCreate(tagName);
```

## 获得标签列表
```java
List<WxUserTag> res = this.wxService.getUserTagService().tagGet();
```

## 更新标签名
```java
Boolean res = this.wxService.getUserTagService().tagUpdate(tagId, tagName);
```
