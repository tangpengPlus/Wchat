## 创建自定义菜单
```java
WxMenu wxMenu = new WxMenu();
// 设置菜单
wxMpService.getMenuService().menuCreate(wxMenu);
```

## 删除自定义菜单
```java
wxMpService.getMenuService().menuDelete();
```

## 获得自定义菜单
```java
WxMenu wxMenu = wxMpService.getMenuService().menuGet();
