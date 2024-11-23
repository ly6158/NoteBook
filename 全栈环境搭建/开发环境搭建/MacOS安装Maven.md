# MacOS 安装 Maven

## 下载直接解压

[下载源码包](https://maven.apache.org/download.cgi)

## 配置文件

> ./maven-path/conf/setting.xml

```xml
<settings>
  <!-- 修改本地仓库路径 -->
  <localRepository>${user.home}/workspace/dependency/maven-repository</localRepository>

  <mirrors>
      <!-- 阿里云镜像 -->
    <mirror>
      <id>alimaven</id>
      <name>aliyun maven</name>
      <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
      <mirrorOf>central</mirrorOf>
    </mirror>
  </mirrors>
</settings>
```

```bash
# Maven环境变量配置
export MAVEN_HOME=/...解压路径/apache-maven-3.6.3
export PATH=$PATH:$MAVEN_HOME/bin
```
