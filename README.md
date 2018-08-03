# Maven Indexd

利用tomcat构建maven中央仓库索引镜像，加速Idea更新仓库索引
1. 下载maven中央仓库索引文件 
* [nexus-maven-repository-index.gz](http://repo1.maven.org/maven2/.index/nexus-maven-repository-index.gz)
* [nexus-maven-repository-index.properties](http://repo1.maven.org/maven2/.index/nexus-maven-repository-index.properties)

2. 替换[src/main/webapp/maven2/.index](file:./src/main/webapp/maven2/.index)下索引文件
3. 执行`mvn tomcat7:run`命令启动服务器
4. windows下运行`notepad C:\Windows\System32\drivers\etc\hosts`命令, linux下执行`vi /etc/hosts`命令，在文件末尾添加代码`127.0.0.1 repo1.maven.org`
5. 在idea中打开`File -> Settings -> Build, Execution, Deployment -> Build Tools -> Maven -> Repositories`， 选中<http://repo1.maven.org/maven2/>, 点击update按钮开始更新索引
6. 还原C:\Windows\System32\drivers\etc\hosts配置

* 对于服务器环境下配置，将项目中的server.xml和tomcat.keystore直接复制到${TOMCAT.HOME}/conf路径下即可

# 附： 
阿里maven镜像
```xml
<mirror>
        <id>nexus-aliyun</id>
        <mirrorOf>central</mirrorOf>
        <name>Nexus aliyun</name>
        <url>http://maven.aliyun.com/nexus/content/groups/public</url>
</mirror>
```
