javax.net.ssl.SSLException: java.security.ProviderException: java.security.KeyException

一般出现此问题的原因是 使用了openjdk，
解决办法： 

1. 换成oracle jdk即可；
1. 或者参考http://blog.csdn.net/yaominhua/article/details/51830630