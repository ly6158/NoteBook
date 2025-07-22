# easytier使用教程

> [官方文档 https://easytier.cn/guide/introduction.html](https://easytier.cn/guide/introduction.html)

## 安装包方式

- [官方下载页面 https://easytier.cn/guide/download.html](https://easytier.cn/guide/download.html)
- 在 **图形界面程序GUI** 列选择下载自己系统对应的安装包
- 安装
- 配置
  - 网络名 name
  - 密钥 password
  - 网络方式
    - 选择手动
    - 链接地址 tcp://127.0.0.1:11010

> ⚠️ 输入链接地址后会出现下拉框，下拉框中的内容是输入的内容，必须要选择才算生效。

## 源码包方式

- [官方下载页面 https://easytier.cn/guide/download.html](https://easytier.cn/guide/download.html)
- 在 **命令行程序CLI** 列选择下载自己系统对应的源码包
- 放置到本机合适的目录
- 进入到 **easytier-core** 所在目录
- 执行命令

```bash
# 启动代理服务
./easytier-core -d --network-name name --network-secret password -p tcp://127.0.0.1:11010
# 查看虚拟网中的节点信息
./easytier-cli peer
# 查看虚拟网路由信息
./easytier-cli route
```
