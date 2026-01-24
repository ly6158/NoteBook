# Mac安装python

##

```bash
# 本机环境安装
brew install python

# 版本管理器 类似于nvm
brew install pyenv

# 安装指定版本python
pyenv install 3.11.10

# 先进入到项目目录 在执行一下命令
pyenv local 3.11.10

# .python-version
```

```bash
# .zshrc
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
```

创建虚拟环境
python -m venv .venv
激活虚拟环境
. .venv/bin/activate
推出虚拟环境
deactivate

pip install uv

```bash
pip install --index-url https://pypi.org/simple/ --extra-index-url https://test.pypi.org/simple/ sqlbot-xpack==0.0.4.84

uv pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple/
```

清华大学
<https://pypi.tuna.tsinghua.edu.cn/simple>
阿里云
<https://mirrors.aliyun.com/pypi/simple/>
