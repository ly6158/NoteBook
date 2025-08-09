# RHEL 安装 ZSH

```bash
# 安装 zsh
yum install -y zsh
# 切换zsh
chsh -s /bin/zsh
# 下载 & 安装 ohmyzsh
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

sh -c "$(curl -fsSL https://gitee.com/mirrors/oh-my-zsh/raw/master/tools/install.sh)"
```

<https://mirrors.tuna.tsinghua.edu.cn/help/ohmyzsh.git/>
