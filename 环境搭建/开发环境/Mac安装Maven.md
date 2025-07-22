# MacOS 安装 Maven

## 下载直接解压

[下载源码包](https://maven.apache.org/download.cgi)

## 配置文件

> ./maven-path/conf/setting.xml

```xml
<settings>
  <!-- 修改本地仓库路径 -->
  <localRepository>${user.home}/workspace/dependency/maven-repository</localRepository>

  <!-- 代理配置 通过配置的代理下载依赖 -->
  <mirrors>
    <!-- 阿里云镜像 -->
    <mirror>
      <id>alimaven</id>
      <mirrorOf>*</mirrorOf>
      <name>阿里云</name>
      <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
      <mirrorOf>central</mirrorOf>
    </mirror>
    <!-- 腾讯云镜像 -->
    <mirror>     
      <id>tencentyun</id>
      <mirrorOf>*</mirrorOf>
      <name>腾讯云</name>
      <url>http://mirrors.cloud.tencent.com/nexus/repository/maven-public/</url>
    </mirror>
  </mirrors>

  <!-- 添加多个仓库 如果第一个仓库未找到依赖会以此在其他仓库中查找 -->
  <profiles>
    <profile>
      <id>china-repository</id>
      <repositories>
        <!-- 腾讯云仓库地址 -->
        <repository>
          <id>tencentyun</id>
          <url>http://mirrors.cloud.tencent.com/nexus/repository/maven-public/</url>
          <releases><enabled>true</enabled></releases>
          <snapshots><enabled>false</enabled></snapshots>
        </repository>
        <!-- 阿里云仓库地址 -->
        <repository>
          <id>aliyun</id>
          <url>https://maven.aliyun.com/repository/public/</url>
          <releases><enabled>true</enabled></releases>
          <snapshots><enabled>false</enabled></snapshots>
        </repository> 
      </repositories>
    </profile>
  </profiles>

  <activeProfiles>
  <activeProfile>china-repository</activeProfile>
  </activeProfiles>
</settings>
```

```bash
# Maven环境变量配置
export MAVEN_HOME=/...解压路径/apache-maven-3.6.3
export PATH=$PATH:$MAVEN_HOME/bin

# 验证
mvn -version
```
