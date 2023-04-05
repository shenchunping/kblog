---
title: Homebrew 常用命令-Mac
toc: true
date: 2019-04-12 13:33:36
tags:
  - Mac
  - brew
categories:
  - Mac

---

# 管理软件包

```shell
    brew --help         #简洁命令帮助
    man brew           #完整命令帮助
    brew install git    #安装软件包(这里是示例安装的Git版本控制)
    brew uninstall git #卸载软件包
    brew search git    #搜索软件包
    brew list             #显示已经安装的所有软件包
    brew update      #同步远程最新更新情况，对本机已经安装并有更新的软件用*标明
    brew outdated      #查看已安装的哪些软件包需要更新
    brew upgrade git   #更新单个软件包
    brew info git      #查看软件包信息
    brew home git      #访问软件包官方站
    brew cleanup       #清理所有已安装软件包的历史老版本
    brew cleanup git   #清理单个已安装软件包的历史版本
```

# 管理服务

```shell
brew services list  # 查看使用brew安装的服务列表
brew services run formula|--all  # 启动服务（仅启动不注册）
brew services start formula|--all  # 启动服务，并注册
brew services stop formula|--all   # 停止服务，并取消注册
brew services restart formula|--all  # 重启服务，并注册
brew services cleanup  # 清除已卸载应用的无用的配置

```

# 自动删除依赖

```shell
# 安装rmtree
brew tap beeftornado/rmtree

# 删除
brew rmtree package
```

# 国内源直接安装

```shell
/bin/bash -c "$(curl -fsSL https://cdn.jsdelivr.net/gh/ineo6/homebrew-install/install.sh)"
```

# 国内源替换

```shell
中科大镜像 https://mirrors.ustc.edu.cn/
清华镜像 https://mirrors.tuna.tsinghua.edu.cn/#
北京外国语镜像 https://mirrors.bfsu.edu.cn/#
```

# 查看brew当前源

```shell
cd "$(brew --repo)" && git remote -v
```

# 查看brew-core当前源

```shell
cd "$(brew --repo homebrew/core)" && git remote -v
```

# 替换源

```shell
# 替换brew
cd "$(brew --repo)" && git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

# 替换homebrew-core
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core" && git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

# 替换homebrew-cask
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-cask" && git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git

# 替换bottles
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.zshrc

# 使其生效
source ~/.bash_profile
```
