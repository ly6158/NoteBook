# RHEL 安装 FRP

## 下载

## 安装

```bash
# 解压
tar -zxvf frp_0.63.0_linux_amd64.tar.gz
```

## 服务端配置

### 配置文件

```toml
# GUI 界面配置
webServer.addr = "0.0.0.0"
webServer.port = 7001
webServer.user = "用户名"
webServer.password = "密码"
```

### 注册到 `systemctl` 托管

```bash
vim /etc/systemd/system/frp.service
```

```bash
[Unit]
Description=Frp Server Service
After=network.target

[Service]
Type=simple
User=root
Restart=on-failure
RestartSec=5s
ExecStart=/root/software/frp/frps -c /root/software/frp/frps.toml

[Install]
WantedBy=multi-user.target
```

```bash
sudo systemctl enable frp
sudo systemctl start frp
sudo systemctl status frp
sudo systemctl restart frp
sudo systemctl stop frp
```

```bash
# 查看启动日志
journalctl -u frp.service

# 修改 SELinux 运行模式
# 0 宽容模式
sudo setenforce 0
```
