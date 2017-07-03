目前cp和mp均支持多种http框架（apache-httpclient、jod-http以及okhttp）的自由选用，
客户端默认情况下可以使用apache httpclient；

拿MP举例子来说：

1、 如果想使用jodd-http，请在项目pom文件中如下配置：
```
        <dependency>
            <groupId>com.github.binarywang</groupId>
            <artifactId>weixin-java-mp</artifactId>
            <version>${weixin-java-mp.version}</version>
            <exclusions>
                <exclusion>
                    <groupId>org.apache.httpcomponents</groupId>
                    <artifactId>*</artifactId>
                </exclusion>
            </exclusions>
        </dependency>

        <dependency>
            <groupId>org.jodd</groupId>
            <artifactId>jodd-http</artifactId>
            <version>3.7.1</version>
        </dependency>
```
此时应该使用的 `WxMpService`实现类应该是：
 `me.chanjar.weixin.mp.api.impl.WxMpServiceJoddHttpImpl`;

也可以参考https://github.com/wechat-group/weixin-java-mp-demo 的jodd-http分支，来查看相关代码。

2、如果想使用okhttp，请在项目pom文件中如下配置：
```
        <dependency>
            <groupId>com.github.binarywang</groupId>
            <artifactId>weixin-java-mp</artifactId>
            <version>${weixin-java-mp.version}</version>
            <exclusions>
                <exclusion>
                    <groupId>org.apache.httpcomponents</groupId>
                    <artifactId>*</artifactId>
                </exclusion>
            </exclusions>
        </dependency>

        <dependency>
            <groupId>com.squareup.okhttp3</groupId>
            <artifactId>okhttp</artifactId>
            <version>3.7.0</version>
        </dependency>
```
此时应该使用的 `WxMpService`实现类应该是：
 `me.chanjar.weixin.mp.api.impl.WxMpServiceOkHttpImpl`;

也可以参考https://github.com/wechat-group/weixin-java-mp-demo 的okhttp分支，来查看相关代码。