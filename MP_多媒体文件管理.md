## 上传多媒体文件
```java
InputStream inputStream = ...;
File file = ...;
WxMediaUploadResult res = wxMpService.mediaUpload(mediaType, fileType, inputStream);
// 或者
res = wxMpService.mediaUpload(mediaType, file);
res.getType();
res.getCreatedAt();
res.getMediaId();
res.getThumbMediaId();
```

## 下载多媒体文件
```java
// 获得一个在系统临时目录的文件
File file = wxMpService.mediaDownload(media_id);
```
