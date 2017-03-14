SPA方式的应用的路径类似这样：
http://example.com/#!/cart/index

android版本的微信会把 #！后面的也做为路径，造成支付失败。
解决方案，添加 ?1=1
http://example.com/?1=1#!/cart/index

详细看这个帖子：http://www.tuicool.com/articles/mQ7RRfb