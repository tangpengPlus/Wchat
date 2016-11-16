在某些环境下，应用程序必须通过代理才能够访问微信接口，比如阿里的ACE（ACE线上环境不能直接访问外网。 HTTP请求需要通过使用代理：
http://ace.aliapp.com/java/quick-start.md?spm=5176.383729.9.2.6HqPoT&file=quick-start.md）。

你可以在构造自己的``WxMpConfigStorage``的时候设置http代理信息：

1. httpPoxyHost
1. httpProxyPort
1. httpProxyUsername（可选）
1. httpProxyPassword（可选）

只要你设置了http代理，那么所有的请求都会从代理走。