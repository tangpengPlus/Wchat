本项目是由个人兴趣发起的项目，所以有时候会比微信官方开放的api要慢一些，如果急着需要使用某个api的话，可以直接使用``WxMpService``的下列3个方法来救急：

1. ``String get(String url, String queryParam) throws WxErrorException;``
1. ``String post(String url, String postData) throws WxErrorException;``
1. ``public <T, E> T execute(RequestExecutor<T, E> executor, String uri, E data) throws WxErrorException;``

这三个方法都带有自动刷新access_token和遇到errcode抛出``WxErrorException``的功能，所以使用的时候只需专注于业务实现就行了。

``get``和``post``方法返回的是``String``，也就是微信服务器返回的内容。你可以拿这个``String``返回值自己处理。

或者使用比较高级的``execute``方法，``T``是返回值类型，``E``是参数类型，可以参考项目里的``mediaUpload``方法：

```java
  public WxMediaUploadResult mediaUpload(String mediaType, File file) throws WxErrorException {
    String url = "http://file.api.weixin.qq.com/cgi-bin/media/upload?type=" + mediaType;
    return execute(new MediaUploadRequestExecutor(), url, file);
  }
```

```java
public class MediaUploadRequestExecutor implements RequestExecutor<WxMediaUploadResult, File> {

  @Override
  public WxMediaUploadResult execute(CloseableHttpClient httpclient, HttpHost httpProxy, String uri, File file) throws WxErrorException, ClientProtocolException, IOException {
    HttpPost httpPost = new HttpPost(uri);
    if (httpProxy != null) {
      RequestConfig config = RequestConfig.custom().setProxy(httpProxy).build();
      httpPost.setConfig(config);
    }
    if (file != null) {
      HttpEntity entity = MultipartEntityBuilder
            .create()
            .addBinaryBody("media", file)
            .build();
      httpPost.setEntity(entity);
      httpPost.setHeader("Content-Type", ContentType.MULTIPART_FORM_DATA.toString());
    }
    CloseableHttpResponse response = httpclient.execute(httpPost);
    String responseContent = Utf8ResponseHandler.INSTANCE.handleResponse(response);
    WxError error = WxError.fromJson(responseContent);
    if (error.getErrorCode() != 0) {
      throw new WxErrorException(error);
    }
    return WxMediaUploadResult.fromJson(responseContent);
  }

}
```

