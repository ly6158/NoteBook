# RHEL 安装 NodeJS

## 源码方式安装

```bash
# 依赖包下载
yum install wget -y

# 下载源码包
wget https://nodejs.org/dist/v18.20.4/node-v18.20.4-linux-x64.tar.xz

# 解压源码包
tar -xvJf node-v18.20.4-linux-x64.tar.xz

# 移动系统目录下
mv node-v18.20.4-linux-x64 /usr/local/node

# 打开配置文件
vim .zshrc

# 添加
export PATH=$PATH:'/usr/local/node/bin'

# 使配置生效
source .zshrc

# npm 切换源
npm config set registry https://registry.npmmirror.com

# 安装pm2 yarn
npm install pm2 yarn -g

# yarn切换源
yarn config set registry https://registry.npmmirror.com

```
