1. 新增的永久素材也可以在公众平台官网素材管理模块中看到
1. 永久素材的数量是有上限的，请谨慎新增。图文消息素材和图片素材的上限为5000，其他类型为1000
1. 素材的格式大小等要求与公众平台官网一致。具体是，图片大小不超过2M，支持bmp/png/jpeg/jpg/gif格式，语音大小不超过5M，长度不超过60秒，支持mp3/wma/wav/amr格式
1. 调用该接口需https协议
1. 永久图片素材新增后，将带有URL返回给开发者，开发者可以在腾讯系域名内使用（腾讯系域名外使用，图片将被屏蔽）

*下面所有方法使用方式可以参考测试用例： weixin-java-tools/weixin-java-mp/src/test/java/me/chanjar/weixin/mp/api/WxMpMaterialAPITest.java*

## 添加图文永久素材

*方法名*： materialNewsUpload

*参数*： WxMpMaterialNews news

*返回值*： WxMpMaterialUploadResult 

图文素材支持单图文和多图文，由类 WxMpMaterialNews 进行封装，图文的数据通过类  WxMpMaterialNews.WxMpMaterialNewsArticle 封装。

多图文消息在 WxMpMaterialNews 中调用 addArticle 方法添加多个 WxMpMaterialNewsArticle 对象即可。

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

非图文永久素材由类 WxMpMaterial 封装，对于非视频类的永久素材，构造时传入素材文件对象file和素材名name即可，素材名会显示在公众平台官网素材管理模块中，其余两个字段可设置为null或者空字符串。视频类永久素材需要在构造时传入视频名title和简介introduction，目前已知视频支持mp4格式。

mediaType支持缩略图类型 thumb。

WxMpMaterial 对象的成员变量 name 需要包含文件后缀，否则微信服务器返回错误码。

接口返回 新增素材的 media_id 和 url

```java
WxMpMaterial wxMaterial = new WxMpMaterial();
wxMaterial.setFile(tempFile);
wxMaterial.setName(fileName);
WxMpMaterialUploadResult res = wxService.materialFileUpload(mediaType, wxMaterial); 
```

## 获取图文永久素材

*方法名*： materialNewsInfo

*参数*：
       
+ 素材对象 String media_id

*返回值*： WxMpMaterialNews

根据 media_id 获取图文消息，结果由 WxMpMaterialNews 封装，该类的结构和微信服务器返回的 json 格式数据的结构保持一致。
见 [获取永久素材返回值格式](http://mp.weixin.qq.com/wiki/4/b3546879f07623cb30df9ca0e420a5d0.html)

## 获取图片或声音永久素材

*方法名*： materialImageOrVoiceDownload

*参数*：
       
+ 素材对象 String media_id

*返回值*： InputStream

根据 media_id 获取声音或者图片的输入流。

## 获取视频永久素材

*方法名*： materialVideoInfo

*参数*：
       
+ 素材对象 String media_id

*返回值*： WxMpMaterialVideoInfoResult

根据 media_id 获取视频信息，返回结果中包含视频下载地址。返回结果由类 WxMpMaterialVideoInfoResult 封装，结构和官方接口返回的json保持一致。

```json
{
  "title":"TITLE",
  "description":"DESCRIPTION",
  "down_url":"DOWN_URL",
}
```

## 删除素材

*方法名*： materialDelete

*参数*：
       
+ 素材对象 String media_id

*返回值*： boolean

根据 media_id 删除素材。

## 修改永久图文素材

*方法名*： materialNewsUpdate

*参数*：
       
+ 更新图文对象 WxMpMaterialVideoInfoResult wxMpMaterialVideoInfoResult

*返回值*： boolean

根据更新图文对象更新图文素材，对于多图文消息，如需更新其中某一个，需要设置更新对象中的index属性。见 [修改永久图文素材](http://mp.weixin.qq.com/wiki/4/19a59cba020d506e767360ca1be29450.html)

## 获取素材总数

*方法名*： materialCount

*返回值*： WxMpMaterialCountResult

获取素材总数，返回结果由类 WxMpMaterialCountResult 封装。结构和官方接口返回的json保持一致。

```json
{
  "voice_count":1,
  "video_count":1,
  "image_count":1,
  "news_count":1
}
```

## 根据类别分页获取非图文素材列表

*方法名*： materialFileBatchGet

*参数*：
       
+ 素材类型 String type 素材的类型，图片（image）、视频（video）、语音 （voice）
+ 偏移位置 int offset 从全部素材的该偏移位置开始返回，0表示从第一个素材 返回
+ 返回数量 int count 取值在1到20之间

*返回值*： WxMpMaterialFileBatchGetResult

获取素材总数，返回结构由类 WxMpMaterialFileBatchGetResult 封装。结构和官方接口返回的json保持一致。
见 [获取素材列表](http://mp.weixin.qq.com/wiki/12/2108cd7aafff7f388f41f37efa710204.html)

## 根据类别分页获取图文素材列表

*方法名*： materialNewsBatchGet

*参数*：
       
+ 偏移位置 int offset 从全部素材的该偏移位置开始返回，0表示从第一个素材 返回
+ 返回数量 int count 取值在1到20之间

*返回值*： WxMpMaterialNewsBatchGetResult

获取素材总数，返回结构由类 WxMpMaterialNewsBatchGetResult 封装。结构和官方接口返回的json保持一致。
见 [获取素材列表](http://mp.weixin.qq.com/wiki/12/2108cd7aafff7f388f41f37efa710204.html)