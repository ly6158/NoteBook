# easytier安装教程

## 安装配置

### 自动安装脚本

```bash
# 适用于Linux服务器
wget -O /tmp/easytier.sh "<https://raw.githubusercontent.com/EasyTier/EasyTier/main/script/install.sh>" && sudo bash /tmp/easytier.sh install --gh-proxy <https://ghfast.top/>

# 安装目录
# /opt/easytier
# 配置文件
# /opt/easytier/config/default.conf

# 基础命令
# 查看运行状态
systemctl status easytier@default
# 启动服务
systemctl start easytier@default
# 重启服务
systemctl restart easytier@default
# 停止服务
systemctl stop easytier@default
```

### 源码安装配置

```bash
# 下载源码包

# 中转端 执行启动命令
# private-mode 私有模式 true 验证网络名和密钥 false 公共服务器
# network-name 网络名
# network-secret 密钥
# 默认代理端口 11010
sudo easytier-core --private-mode true --network-name name --network-secret password

# 客户端 启动命令
# network-name 网络名 与中转服务保持一致
# network-secret 密钥 与中转服务保持一致
# -p 中转服务的地址
./easytier-core -d --network-name name --network-secret password -p tcp://127.0.0.1:11010

```

### 启用 systemctl 托管

> 文件路径 /etc/systemd/system/easytier@.service

```bash
[Unit]
Description=EasyTier Service
Wants=network.target
After=network.target network.service
StartLimitIntervalSec=0

[Service]
Type=simple
WorkingDirectory=/opt/easytier
ExecStart=/opt/easytier/easytier-core -c /opt/easytier/config/%i.conf
Restart=always
RestartSec=1s

[Install]
WantedBy=multi-user.target
```

## 中转服务配置

> 具有公网IP

```conf
hostname = "转发节点"
instance_name = "default" # 与启动命令对应 勿改
dhcp = true
listeners = [
    "tcp://0.0.0.0:11010",
    "udp://0.0.0.0:11010",
    "wg://0.0.0.0:11011",
    "ws://0.0.0.0:11011/",
    "wss://0.0.0.0:11012/",
]
exit_nodes = []
rpc_portal = "0.0.0.0:0"

[network_identity]
network_name = "name" # 网络名
network_secret = "password" # 密钥

[flags]
private_mode = true # 开启
default_protocol = "udp"
dev_name = ""
enable_encryption = true
enable_ipv6 = true
mtu = 1380
latency_first = false
enable_exit_node = false
no_tun = false
use_smoltcp = false
foreign_network_whitelist = "*"
disable_p2p = false
relay_all_peer_rpc = false
disable_udp_hole_punching = false
```

## 公司服务配置

```conf
hostname = "公司节点"
instance_name = "default" # 与启动命令对应 勿改
dhcp = true
listeners = [
    "tcp://0.0.0.0:11010",
    "udp://0.0.0.0:11010",
    "wg://0.0.0.0:11011",
    "ws://0.0.0.0:11011/",
    "wss://0.0.0.0:11012/",
]
exit_nodes = []
rpc_portal = "0.0.0.0:0"

[[peer]]
uri = "tcp://127.0.0.1:11010" # 初始连接到中转服务

[network_identity]
network_name = "name" # 与中转服务配置的网络名一致
network_secret = "password" # 与与中转服务配置的密钥一致

[[proxy_network]]
cidr = "192.168.8.0/24" # 转发本地网段

[flags]
default_protocol = "udp"
dev_name = ""
enable_encryption = true
enable_ipv6 = true
mtu = 1380
latency_first = false
enable_exit_node = false
no_tun = false
use_smoltcp = false
foreign_network_whitelist = "*"
disable_p2p = false
relay_all_peer_rpc = false
disable_udp_hole_punching = false
```
