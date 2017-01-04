请检查本地项目jar包版本，是否与本SDK所依赖的版本（https://raw.githubusercontent.com/wechat-group/weixin-java-tools/master/pom.xml ）一致，一般来说是由于部分jar包版本过低导致。
最常见的是httpclient的版本问题，请检查并核实，手动在本地maven pom文件中指定其版本号。