1. 新增的永久素材也可以在公众平台官网素材管理模块中看到
1. 永久素材的数量是有上限的，请谨慎新增。图文消息素材和图片素材的上限为5000，其他类型为1000
1. 素材的格式大小等要求与公众平台官网一致。具体是，图片大小不超过2M，支持bmp/png/jpeg/jpg/gif格式，语音大小不超过5M，长度不超过60秒，支持mp3/wma/wav/amr格式
1. 调用该接口需https协议
1. 永久图片素材新增后，将带有URL返回给开发者，开发者可以在腾讯系域名内使用（腾讯系域名外使用，图片将被屏蔽）

## 添加图文永久素材

*方法名*： materialNewsUpload

*参数*： WxMpMaterialNews news

*返回值*： WxMpMaterialUploadResult 

图文素材支持单图文和多图文，由类 WxMpMaterialNews 进行封装，图文的数据通过类  WxMpMaterialNews.WxMpMaterialNewsArticle 封装。

多图文消息在 WxMpMaterialNews 中调用 addArticle 方法添加多个 WxMpMaterialNewsArticle 对象即可，具体参考 me/chanjar/weixin/mp/api/WxMpMaterialAPITest.java 测试用例中的 testAddNews 方法。

接口返回 新增图文消息的media_id

```java
    // 单图文消息的例子
    WxMpMaterialNews wxMpMaterialNewsSingle = new WxMpMaterialNews();
    WxMpMaterialNews.WxMpMaterialNewsArticle mpMaterialNewsArticleSingle = 
new WxMpMaterialNews.WxMpMaterialNewsArticle();
    mpMaterialNewsArticleSingle.setAuthor("author");
    mpMaterialNewsArticleSingle.setThumbMediaId(thumbMediaId);
    mpMaterialNewsArticleSingle.setTitle("single title");
    mpMaterialNewsArticleSingle.setContent("single content");
    mpMaterialNewsArticleSingle.setContentSourceUrl("content url");
    mpMaterialNewsArticleSingle.setShowCoverPic(true);
    mpMaterialNewsArticleSingle.setDigest("single news");
    wxMpMaterialNewsSingle.addArticle(mpMaterialNewsArticleSingle);
    WxMpMaterialUploadResult resSingle =
 wxService.materialNewsUpload(wxMpMaterialNewsSingle);
```

## 添加其他类型永久素材

*方法名*： materialFileUpload

*参数*：

+ 素材文件类型 String mediaType         
+ 素材对象 WxMpMaterial material

*返回值*： WxMpMaterialUploadResult


图片和音频素材的限制参考上方的注意事项。

非图文永久素材由类 WxMpMaterial 封装，对于非视频类的永久素材，构造时传入素材文件对象file和素材名name即可，素材名会显示在公众平台官网素材管理模块中，其余两个字段可设置为null或者空字符串。视频类永久素材需要在构造时传入视频名title和简介introduction。

mediaType支持缩略图类型 thumb。

WxMpMaterial 对象的成员变量 name 需要包含文件后缀，否则微信服务器返回错误码。

接口返回 新增素材的 media_id 和 url

```java
WxMpMaterial wxMaterial = new WxMpMaterial();
wxMaterial.setFile(tempFile);
wxMaterial.setName(fileName);
WxMpMaterialUploadResult res = wxService.materialFileUpload(mediaType, wxMaterial); 
```