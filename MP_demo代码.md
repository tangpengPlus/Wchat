关于demo项目请参考项目首页相关部分的说明：https://github.com/Wechat-Group/weixin-java-tools

也可以运行本项目的demo代码来对``weixin-java-tools``的有一个更好的了解。

相关代码在：

1. ``WxMpDemoServer``
2. ``WxMpDemoServlet``

启动方式：

1. 直接运行``WxMpDemoServer``
1. 将``test-config.sample.xml``改成``test-config.xml``，并配置相关信息
1. 运行``ngrok 8080``（[ngrok](https://ngrok.com/)是一个让外网访问本机的工具）

    运行``ngrok``后会出现类似下面的信息：
    ```
    Tunnel Status                 online
    Version                       1.7/1.6
    Forwarding                    http://1bf992b1.ngrok.com -> 127.0.0.1:8080
    Forwarding                    https://1bf992b1.ngrok.com -> 127.0.0.1:8080
    Web Interface                 127.0.0.1:4040
    # Conn                        52
    Avg Conn Time                 97.88ms
    ```

    以后访问http://1bf992b1.ngrok.com 就等于访问 http://localhost:8080。
1. 将这个地址改为的公众号的服务器地址，然后就可以调试运行了。
