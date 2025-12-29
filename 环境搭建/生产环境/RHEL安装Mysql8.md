# 安装 mysql8 & 依赖

```bash
# 防火墙放行3306端口
sudo firewall-cmd --zone=public --add-port=3306/tcp --permanent

# 重载防火墙
sudo firewall-cmd --reload

# 更新GPG密钥
rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2023

# 下载 Repo 源
sudo dnf install -y https://dev.mysql.com/get/mysql80-community-release-el9-3.noarch.rpm

# 安装包
sudo dnf install -y mysql-server

# 将mysql设为开机启动项
systemctl enable mysqld

# 启动服务
systemctl start mysqld

# 查看MySQL初始默认密码
sudo grep 'temporary password' /var/log/mysqld.log

# 查看是否启动MySQL服务
ps -ef|grep mysql
```
