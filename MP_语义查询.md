```java
WxMpSemanticQuery semanticQuery = new WxMpSemanticQuery();
semanticQuery.setQuery(...);
semanticQuery.setCategory(...);
semanticQuery.setLatitude(...);
semanticQuery.setLongitude(...);
semanticQuery.setCity(...);
semanticQuery.setAppid(...);
semanticQuery.setUid(...);

WxMpSemanticQueryResult result = semanticQuery(semanticQuery);
```