# RHEL 安装 FRP

```bash
tar -zxvf frp_0.63.0_linux_amd64.tar.gz
```

```toml
webServer.addr = "0.0.0.0"
webServer.port = 7001
webServer.user = "liuyang"
webServer.password = "Liuyang0!"
```


vim /etc/systemd/system/frp.service

[Unit]
Description=Frp Server Service
After=network.target

[Service]
Type=simple
User=root
Restart=on-failure
RestartSec=5s
ExecStart=/root/software/frp/frpc -c /root/software/frp/frpc.toml

[Install]
WantedBy=multi-user.target


sudo systemctl enable frp
sudo systemctl start frp
sudo systemctl status frp
sudo systemctl restart frp
sudo systemctl stop frp

journalctl -u frp.service