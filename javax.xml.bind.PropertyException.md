
在1.1.0之前的版本，如果开发环境使用的是Open JDK会出现类似下面的错误：

```
javax.xml.bind.PropertyException: name: com.sun.xml.internal.bind.marshaller.CharacterEscapeHandler value: me.chanjar.weixin.mp.util.xml.XmlTransformer$CharacterUnescapeHandler@82a9728
```

解决办法是使用OracleJDK。

从1.1.0开始把JAXB替换为了xstream，就不会再有这个错误了。
