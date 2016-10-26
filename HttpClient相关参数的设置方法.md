## 1.修改HttpClient链接参数配置

为了方便HttpClient相关参数的配置增加了接口ApacheHttpClientBuilder并实现了一个默认配置DefaultApacheHttpClientBuilder.在默认配置中具体的配置参数如下:

```java
  private int connectionRequestTimeout = 3000;//从连接池获取链接的超时时间设置,默认3000ms
  private int connectionTimeout = 5000;//建立链接的超时时间,默认5000ms.(由于使用了连接池,这个参数没有实际意义)
  private int soTimeout = 5000;//连接池socket超时时间,默认5000ms
  private int idleConnTimeout = 60000;//空闲链接的超时时间,默认60000ms
  private int checkWaitTime = 60000;//空闲链接的检测周期,默认60000ms
  private int maxConnPerHost = 10;//每路最大连接数,默认10
  private int maxTotalConn = 50;//连接池最大连接数,默认50
  private String userAgent;//HttpClient请求时使用的User Agent(默认为HttpClient的默认值)
```

参考[MP_Quick Start](https://github.com/wechat-group/weixin-java-tools/wiki/MP_Quick-Start)或者[CP_Quick-Start](https://github.com/wechat-group/weixin-java-tools/wiki/CP_Quick-Start)在API初始化是我们需要设置Wx\*\*ConfigStorage,可以通过方法#setApacheHttpClientBuilder设置ApacheHttpClientBuilder的实现类来配置具体的HttpClient的参数配置.默认没有设置本参数的时候将会使用DefaultApacheHttpClientBuilder中默认的参数配置.下面以DefaultApacheHttpClientBuilder为例给出修改参数的配置方法



```java
Wx**InMemoryConfigStorage config = new Wx**InMemoryConfigStorage();
config.setHttpProxyHost(..);//设置代理地址,没有可以无需设置
config.setHttpProxyPort(..);//设置代理端口,没有可以无需设置
config.setHttpProxyUsername(..);//设置代理用户名,没有可以无需设置
config.setHttpProxyPassword(..);//设置代理密码,没有可以无需设置

DefaultApacheHttpClientBuilder clientBuilder = DefaultApacheHttpClientBuilder.get();
clientBuilder.setConnectionRequestTimeout(..)//从连接池获取链接的超时时间(单位ms)
clientBuilder.setConnectionTimeout(..)//建立链接的超时时间(单位ms)
clientBuilder.setSoTimeout(..)//连接池socket超时时间(单位ms)
clientBuilder.setIdleConnTimeout(..)//空闲链接的超时时间(单位ms)
clientBuilder.setCheckWaitTime(..)//空闲链接的检测周期(单位ms)
clientBuilder.setMaxConnPerHost(..)//每路最大连接数
clientBuilder.setMaxTotalConn(..)//连接池最大连接数
clientBuilder.setUserAgent(..)//HttpClient请求时使用的User Agent
config.setApacheHttpClientBuilder(clientBuilder); //设置自定义的ApacheHttpClientBuilder

```

## 2.关于在spring中的使用

方法一,可以自己实现ApacheHttpClientBuilder接口然后在Wx\*\*ConfigStorage中设置.**推荐此方法**

方法二,使用DefaultApacheHttpClientBuilder,考虑到DefaultApacheHttpClientBuilder并不是最优解,所以没有提供public的构造方法,只提供了一个静态方法获取实例.如果一定要使用这个类来实现自定义配置的话我们需要定义一个Spring的FactoryBean,下面给出参考代码.

```java
import org.springframework.beans.factory.FactoryBean;
import me.chanjar.weixin.common.util.http.ApacheHttpClientBuilder;
import me.chanjar.weixin.common.util.http.DefaultApacheHttpClientBuilder;


public class DefaultApacheHttpClientBuilderFactoryBean implements FactoryBean<ApacheHttpClientBuilder> {
  private int connectionRequestTimeout;
  private int connectionTimeout;
  private int soTimeout;
  private int idleConnTimeout;
  private int checkWaitTime;
  private int maxConnPerHost;
  private int maxTotalConn;
  private String userAgent;
  
  public ApacheHttpClientBuilder getObject() throws Exception {
    DefaultApacheHttpClientBuilder clientBuilder = DefaultApacheHttpClientBuilder.get();
    clientBuilder.setConnectionRequestTimeout(this.connectionRequestTimeout);
    clientBuilder.setConnectionTimeout(this.connectionTimeout);
    clientBuilder.setSoTimeout(this.soTimeout);
    clientBuilder.setIdleConnTimeout(this.idleConnTimeout);
    clientBuilder.setCheckWaitTime(this.checkWaitTime);
    clientBuilder.setMaxConnPerHost(this.maxConnPerHost);
    clientBuilder.setMaxTotalConn(this.maxTotalConn);
    clientBuilder.setUserAgent(this.userAgent);
    return clientBuilder;
  }

  public Class<?> getObjectType(){
    return ApacheHttpClientBuilder.class;
  }

  public boolean isSingleton(){
    return true;
  }

  public void setConnectionRequestTimeout(int connectionRequestTimeout) {
    this.connectionRequestTimeout = connectionRequestTimeout;
  }

  public void setConnectionTimeout(int connectionTimeout) {
    this.connectionTimeout = connectionTimeout;
  }

  public void setSoTimeout(int soTimeout) {
    this.soTimeout = soTimeout;
  }

  public void setIdleConnTimeout(int idleConnTimeout) {
    this.idleConnTimeout = idleConnTimeout;
  }

  public void setCheckWaitTime(int checkWaitTime) {
    this.checkWaitTime = checkWaitTime;
  }

  public void setMaxConnPerHost(int maxConnPerHost) {
    this.maxConnPerHost = maxConnPerHost;
  }

  public void setMaxTotalConn(int maxTotalConn) {
    this.maxTotalConn = maxTotalConn;
  }

  public void setUserAgent(String userAgent) {
    this.userAgent = userAgent;
  }
}

```
