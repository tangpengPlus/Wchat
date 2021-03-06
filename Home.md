# 微信Java SDK开发文档

## 常见问题
1. **在微信后台设置安全域名时，注意不要将http等字符带入，首先要理解域名的含义，应该是`www.abcde.com`类似这样的**
1. [对Maven不熟的，建议学习此视频](http://www.imooc.com/learn/443)
1. [几个内网端口映射服务网站(可以实现将内网主机暴露给外网访问，比如ngrok)](https://github.com/Wechat-Group/weixin-java-tools/wiki/%E5%87%A0%E4%B8%AA%E5%86%85%E7%BD%91%E7%AB%AF%E5%8F%A3%E6%98%A0%E5%B0%84%E6%9C%8D%E5%8A%A1%E7%BD%91%E7%AB%99)
1. [下载maven jar包出现问题时请设置maven镜像库](https://github.com/Wechat-Group/weixin-java-tools/wiki/%E4%B8%8B%E8%BD%BDmaven-jar%E5%8C%85%E5%87%BA%E7%8E%B0%E9%97%AE%E9%A2%98%E6%97%B6%E8%AF%B7%E8%AE%BE%E7%BD%AEmaven%E9%95%9C%E5%83%8F%E5%BA%93)
1. [Emoji表情字符存储有问题，或者遇到保存字符串到数据库里出现`\xF0\x9F\x92\x94`类似问题时，请尝试使用这个工具](https://github.com/binarywang/java-emoji-converter)
1. [httpclient 4.3.1 版本有bug，请不要使用](https://github.com/Wechat-Group/weixin-java-tools/wiki/httpclient-4.3.1-%E7%89%88%E6%9C%AC%E6%9C%89bug-%E8%AF%B7%E4%B8%8D%E8%A6%81%E4%BD%BF%E7%94%A8)

## 常见异常问题的解决办法

1. [加解密时出现`Illegal key size`异常的处理办法](https://github.com/Wechat-Group/weixin-java-tools/wiki/加解密的异常处理办法)
1. [发生`java.security.KeyException`的解决办法](https://github.com/Wechat-Group/weixin-java-tools/wiki/java.security.KeyException)
1. [出现NoClassDefFoundError、NoSuchMethdError或ClassNotFoundException的解决办法](https://github.com/Wechat-Group/weixin-java-tools/wiki/NoClassDefFoundError%E3%80%81NoSuchMethdError%E6%88%96ClassNotFoundException%E7%9A%84%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%95)

## 通用问题

1. [Session](https://github.com/Wechat-Group/weixin-java-tools/wiki/WxSession)
1. [配置日志](https://github.com/Wechat-Group/weixin-java-tools/wiki/配置日志)
1. [消息排重](https://github.com/Wechat-Group/weixin-java-tools/wiki/消息排重)
1. [Http框架的选用说明](https://github.com/Wechat-Group/weixin-java-tools/wiki/http%E6%A1%86%E6%9E%B6%E7%9A%84%E9%80%89%E7%94%A8%E8%AF%B4%E6%98%8E)
1. [HttpClient参数配置](https://github.com/Wechat-Group/weixin-java-tools/wiki/HttpClient相关参数的设置方法)

## 微信支付开发
1. [微信支付官方文档入口](https://pay.weixin.qq.com/wiki/doc/api/index.html)
1. [微信支付Demo项目](https://github.com/binarywang/weixin-java-pay-demo)
1. [微信支付使用说明](https://github.com/Wechat-Group/weixin-java-tools/wiki/%E5%BE%AE%E4%BF%A1%E6%94%AF%E4%BB%98)

## 公众号开发
1. [【微信公众号官方文档入口】](http://mp.weixin.qq.com/wiki)：http://mp.weixin.qq.com/wiki 
1. [Quick Start（快速入门）](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_Quick-Start)
1. [Demo代码及Demo项目](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_demo代码)
1. [微信消息路由器](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_微信消息路由器)
1. [WxMpConfigStorage](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_WxMpConfigStorage)
1. [验证消息合法性](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_验证消息合法性)
1. [消息的加解密](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_消息的加解密)
1. [同步回复消息（被动回复）](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_同步回复消息)
1. [主动发送消息（客服消息）](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_%E4%B8%BB%E5%8A%A8%E5%8F%91%E9%80%81%E6%B6%88%E6%81%AF%EF%BC%88%E5%AE%A2%E6%9C%8D%E6%B6%88%E6%81%AF%EF%BC%89)
1. [永久素材管理](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_永久素材管理)
1. [临时素材（多媒体文件）管理](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_多媒体文件管理)
1. [用户管理](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_用户管理)
1. [标签管理](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_标签管理)
1. [群发消息](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_群发消息)
1. [自定义菜单管理](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_自定义菜单管理)
1. [二维码管理](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_二维码管理)
1. [短链接管理](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_短链接管理)
1. [发送模板消息](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_发送模板消息)
1. [语义查询](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_语义查询)
1. [OAuth2网页授权](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_OAuth2网页授权)
1. [JS_API支持](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_js_api)
1. [http代理支持](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_http代理支持)
1. [如何调用未支持的接口](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_如何调用未支持的接口)
1. [如何执行本项目单元测试](https://github.com/Wechat-Group/weixin-java-tools/wiki/MP_如何执行本项目单元测试)

## 企业号（企业微信）开发
1. [企业号官方文档地址](http://qydev.weixin.qq.com/wiki/index.php)
1. [企业微信官方文档地址](https://work.weixin.qq.com/api/doc)
1. [Quick Start](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_Quick-Start)
1. [微信消息路由器](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_微信消息路由器)
1. [WxCpConfigStorage](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_WxCpConfigStorage)
1. [同步回复消息](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_同步回复消息)
1. [刷新access_token](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_刷新access_token)
1. [用户身份二次验证](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_用户身份二次验证)
1. [主动发送消息](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_主动发送消息)
1. [多媒体文件管理](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_多媒体文件管理)
1. [用户管理](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_用户管理)
1. [部门管理](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_部门管理)
1. [标签管理](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_标签管理)
1. [自定义菜单管理](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_自定义菜单管理)
1. [OAuth2网页授权](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_OAuth2网页授权)
1. [http代理支持](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_http代理支持)
1. [如何调用未支持的接口](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_如何调用未支持的接口)
1. [如何执行本项目单元测试](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_如何执行本项目单元测试)
1. [demo代码](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_demo代码)
1. [如何支持多个企业号应用，或者支持多个企业号](https://github.com/Wechat-Group/weixin-java-tools/wiki/CP_如何支持多个企业号应用或企业号)
