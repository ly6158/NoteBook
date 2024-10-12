# RHEL 常用命令

```bash
# SSH记住登录凭证
ssh-copy-id -i ~/.ssh/id_rsa.pub root@ip

# SSH清除连接认证
ssh-keygen -R <IP>

查看应用进程 (tomcat为例)
ps -ef | grep tomcat

# 作为服务启动 (tomcat为例)
nohup ./startup.sh > ../logs/catalina.out 2>&1 &

# 动态查看日志
tail -f catalina.out

# 防火墙添加端口 以端口3000为例
sudo firewall-cmd --zone=public --add-port=3306/tcp --permanent

# 防火墙配置文件
vim /etc/sysconfig/iptables

# 重启防火墙
/etc/init.d/iptables restart
sudo firewall-cmd --reload

# 建立软连接
ln -s ~/software/node-v16.18.1/bin/node /usr/bin/node

# 更新替换软连接
ln -snf ~/software/node-v16.18.1/bin/node /usr/bin/node

```
