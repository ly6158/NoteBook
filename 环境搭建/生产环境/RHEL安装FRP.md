# RHEL 安装 FRP

## 下载

[官方文档](https://gofrp.org/zh-cn/)

## 安装

```bash
# 解压
tar -zxvf frp_0.63.0_linux_amd64.tar.gz
```

## 启动

```bash
# 服务端启动命令
./frp/frps -c ./frp/frps.toml
# 客户端启动命令
./frp/frpc -c ./frp/frpc.toml
```

## `systemctl` 托管

> vim /etc/systemd/system/frp.service

```conf
[Unit]
Description=Frp Server Service
After=network.target

[Service]
Type=simple
User=root
Restart=on-failure
RestartSec=5s
# 服务端启动命令
ExecStart=/root/software/frp/frps -c /root/software/frp/frps.toml

[Install]
WantedBy=multi-user.target
```

```bash
# 开机自启
sudo systemctl enable frp
# 启动
sudo systemctl start frp
# 查看状态
sudo systemctl status frp
# 重启
sudo systemctl restart frp
# 停止
sudo systemctl stop frp
```

## 服务端配置

> `./frp/frps.toml`

```toml
# GUI 界面配置
webServer.addr = "0.0.0.0"
webServer.port = 7001
webServer.user = "用户名"
webServer.password = "密码"
```

## 客户端配置

> `./frp/frpc.toml`

```toml
# 服务端 IP
serverAddr = "127.0.0.1"
# 服务端 端口
serverPort = 7000

# GUI 界面配置
webServer.addr = "0.0.0.0"
webServer.port = 7001
webServer.user = "用户名"
webServer.password = "密码"
```

## 其他

```bash
# 查看启动日志
journalctl -u frp.service

# 修改 SELinux 运行模式
# 0 宽容模式
sudo setenforce 0
```
