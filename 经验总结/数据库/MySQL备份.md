# MySQL 数据备份

## 安装客户端

```bash
# 更新GPG密钥
rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2023

# 下载 Repo 源
sudo dnf install -y https://dev.mysql.com/get/mysql80-community-release-el9-3.noarch.rpm

# 安装 MySQL 客户端
sudo dnf install mysql-community-client
```

## 备份脚本

```bash
# 日期格式 $(date +'%Y_%m_%d_%H_%M_%S')
/usr/bin/mysqldump -h [地址] -u [用户名] -p[密码] --single-transaction --routines --triggers --databases [数据库名] > /path/backup_$(date +'%Y_%m_%d_%H_%M_%S').sql
```

## 自动脚本

### 新建脚本文件

> backup.sh

```bash
# 将上诉 备份脚本 添加到 backup.sh 文件中

# 授予执行权限
chmod +x backup.sh
```

### 添加到系统任务

```bash
# 编辑任务
crontab -e

# 每天0点执行
0 0 * * * /root/bash/backup_oa.sh >> /root/backup/logs/backup_oa.log 2>&1
```
