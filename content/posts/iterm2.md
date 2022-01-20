---
title: "M1 Mac - 我也想要漂漂的終端機... iTerm2 + Oh My Zsh + Powerlevel10k 實作"
date: 2021-07-27T21:54:25+08:00
tags:
- 開發
- macOS
- iTerm2
- Oh My Zsh
- Powerlevel10k
categories:
- 軟體
author: "小雷"
showToc: true
TocOpen: true
draft: false
hidemeta: false
comments: false
disableShare: false
disableHLJS: false
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
---

好久沒用 Mac 了。  
回來的第一件事情就是來把終端機弄漂亮這樣工作起來心情比較愉悅（？

## 安裝 Homebrew

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-07-27%20%E4%B8%8B%E5%8D%889.42.25.png)

Homebrew 是 macOS 的一個 Package Manager，我們會透過它來安裝各式各樣的軟體跟套件。

打開終端機輸入指令

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

他就會自動裝好了。（然後回頭一看才發現好像用不太到www 算了）

## 安裝 iTerm2

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-07-27%20%E4%B8%8B%E5%8D%889.31.33.png)

其實 Mac 的 terminal 沒有那麼好用，所以大家都用第三方的 iTerm2

由於 ARM 版的 Homebrew 沒有 cask 能用，所以沒辦法用指令安裝。  
因此我們就直接上官網抓吧

https://iterm2.com/downloads.html

## 安裝 Oh My Zsh

這個是一個 zsh 外掛，提供更細部的修正以及佈景主題功能

由於 macOS Big Sur 已經內建 zsh 了  
所以我們就直接跳過 zsh 的安裝直接來裝 Oh My Zsh。

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

安裝結束之後預設終端機會被覆蓋掉，重新啟動 iTerm2 即可

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-07-27%20%E4%B8%8B%E5%8D%883.55.11.png)

## 安裝 Powerlevel10k

這個是 Oh My Zsh 的超高自訂性終極佈景主題

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

下載結束後進行初次設定

```bash
p10k configure
```
安裝程式會發現沒有安裝字型，這邊會將字體設定好並套用到 iTerm2

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-07-27%20%E4%B8%8B%E5%8D%884.20.43.png)

途中有一些字體測試，就按照著步驟做過去就行了

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-07-27%20%E4%B8%8B%E5%8D%884.21.13.png)

最後就是一系列的外觀設定

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-07-27%20%E4%B8%8B%E5%8D%884.21.36.png)

存擋設定至 ~/.zshrc 裏面

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-07-27%20%E4%B8%8B%E5%8D%884.24.37.png)

## 自動補全與語法凸顯

歷史指令自動補全

```bash
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

語法凸顯外掛
```bash
git clone git://github.com/zsh-users/zsh-syntax-highlighting $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
```

最後用任何編輯器（如 vim）打開 ~/.zshrc，將 Plugin 裡面修改成這樣

```bash
plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
)
```

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-07-27%20%E4%B8%8B%E5%8D%884.28.11.png)

---

做到這邊就有美美漂亮的終端機可以用了

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-07-27%20%E4%B8%8B%E5%8D%889.45.15.png)