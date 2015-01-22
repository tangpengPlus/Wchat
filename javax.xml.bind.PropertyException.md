当使用OpenJDK开发的时候，会出现类似下面的错误：

```
javax.xml.bind.PropertyException: name: com.sun.xml.internal.bind.marshaller.CharacterEscapeHandler value: me.chanjar.weixin.mp.util.xml.XmlTransformer$CharacterUnescapeHandler@82a9728
```

目前的解决办法是使用OracleJDK。