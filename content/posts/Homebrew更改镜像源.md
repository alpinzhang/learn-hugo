---
title: "Homebrew更改镜像源"
date: 2023-06-18T15:47:25+08:00
draft: false
---

> 本文配置针对 mac `.zsh` 的用户，其他 sh 用户可改成对应的配置  

### 修改`bottles`源
bottles 源：Homebrew 预编译二进制软件包。
```bash
# 中科大
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.zshrc

# 清华：
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.zshrc

# 还原
# 进入到 ~/.zshrc 中注释掉 HOMEBREW_BOTTLE_DOMAIN 即可还原为官方源

# 修改源后，重新加载配置
source ~/.zshrc
```

### 查看仓库的源
```bash
git -C "$(brew --repo)" remote -v
```

### 替换为中科大的源
```bash
# 替换 Homebrew
git -C "$(brew --repo)" remote set-url origin https://mirrors.ustc.edu.cn/brew.git

# 替换 Homebrew Core
git -C "$(brew --repo homebrew/core)" remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git

# 替换 Homebrew Cask
git -C "$(brew --repo homebrew/cask)" remote set-url origin https://mirrors.ustc.edu.cn/homebrew-cask.git

# 更新
brew update
```

### 替换为清华的源
```bash
# 替换 Homebrew
git -C "$(brew --repo)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

# 替换 Homebrew Core
git -C "$(brew --repo homebrew/core)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

# 替换 Homebrew Cask
git -C "$(brew --repo homebrew/cask)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git

# 更新
brew update
```

### 还原
```bash
git -C "$(brew --repo)" remote set-url origin https://github.com/Homebrew/brew.git

git -C "$(brew --repo homebrew/core)" remote set-url origin https://github.com/Homebrew/homebrew-core.git

git -C "$(brew --repo homebrew/cask)" remote set-url origin https://github.com/Homebrew/homebrew-cask.git

brew update
```