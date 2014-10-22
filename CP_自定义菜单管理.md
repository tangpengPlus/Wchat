## 创建自定义菜单
```java
WxMenu wxMenu = new WxMenu();
// 设置菜单
wxCpService.menuCreate(wxMenu);
```

## 删除自定义菜单
```java
wxCpService.menuDelete();
```

## 获得自定义菜单
```java
WxMenu wxMenu = wxCpService.menuGet()
