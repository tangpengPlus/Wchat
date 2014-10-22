## 新建部门

```java
WxCpDepart depart = new WxCpDepart();
depart.setName("子部门" + System.currentTimeMillis());
depart.setParentId(1);
depart.setOrder(1);
Integer departId = wxCpService.departCreate(depart);
```

## 获取部门

```java
List<WxCpDepart> departList = wxCpService.departGet();
```

## 更新部门

```java
depart.setName("子部门改名" + System.currentTimeMillis());
wxCpService.departUpdate(depart);
```

## 删除部门

```java
wxCpService.departDelete(depart.getId());
```
