# RHEL 安装 Docker

## 下载安装

```bash
# 1. 安装必要工具
sudo dnf install -y dnf-plugins-core

# 2. 添加 Docker 官方仓库
sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

# 3. 安装 Docker
sudo dnf install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# 4. 启动并启用 Docker
sudo systemctl enable --now docker

# 5. 验证
sudo docker --version
```

## 配置代理

> /etc/docker/daemon.json

```conf
{
  "registry-mirrors": [
    "https://docker.m.daocloud.io",
    "https://ccr.ccs.tencentyun.com"
  ]
}
```

### 测试代理服务器是否可用

```bash
ping -c 3 ccr.ccs.tencentyun.com
```

### 修改后重启

```bash
sudo systemctl daemon-reload
sudo systemctl restart docker
```
