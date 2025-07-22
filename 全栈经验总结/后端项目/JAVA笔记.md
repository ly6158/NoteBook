# JAVA 笔记

## IDEA相关

- 如果本地安装了Maven需要在IDEA里面将Maven改成本地的

## 代码编译、测试并打包

```bash
mvn clean package -U
```

- `-U`：参数强制 Maven 更新快照依赖

## SpringBoot 命令方式启动

```bash
mvn spring-boot:run
```

## SpringBoot 接口返回乱码

```java
// 加上 produces = { "application/json;charset=UTF-8" }
@RequestMapping(value = "/example", produces = "application/json;charset=UTF-8")
```

## Maven 手动安装依赖

> 以 Oracle JDBC8 为例

```bash
mvn install:install-file -DgroupId=com.oracle -DartifactId=jdbc8 -Dversion=12.2.0.1 -Dpackaging=jar -Dfile=./jdbc8-12.2.0.1.jar
```

- `-DgroupId`：组织或公司名（如 com.oracle），对应 Maven 配置中的 `<groupId>`
- `-DartifactId`：依赖名称（如 jdbc8），对应 Maven 配置中的 `<artifactId>`
- `-Dversion`：版本号（如 12.2.0.1），对应 Maven 配置中的 `<version>`
- `-Dpackaging`：打包类型（如 jar），对应 Maven 配置中的 `<packaging>`
- `-Dfile`：本地 jar 包的路径，无需在 Maven 配置中指定

在 `pom.xml` 中引用：

```xml
<dependency>
  <groupId>com.oracle</groupId>
  <artifactId>jdbc8</artifactId>
  <version>12.2.0.1</version>
  <packaging>jar</packaging>
</dependency>
```

## 老旧项目相关

### 部分依赖无法下载

> 最新的 `Maven` 仓库中不存在就版本的依赖包

- 手动下载 `jar` 包本地安装
- 从其他本地仓库中找到 `jar` 和 `pom` 文件放置到本地 `Maven` 仓库中
  - ⚠️ 注意路径需要保持一致

### 版本不兼容问题

> `pom.xml` 中依赖未指定版本则会下载最新版本，可能会与旧版本JDK不兼容

- 查找与当前JDK版本兼容的依赖版本，并在 `pom.xml` 中指定版本号
