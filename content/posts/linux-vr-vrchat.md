---
title: "嘗試在 Linux 上面玩 VR -> VRChat 篇"
date: 2022-08-29T00:57:21+08:00
tags:
- Linux
- VR
- VRChat
- Valve Index
- Fedora
categories:
- 開發
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

## 環境

- Intel Core i9 12900
- NVidia GeForce RTX 3080
- 32GB DDR4-3200
- Fedora Workstation 36
- Valve Index

## 前言

以前還持有 Quest 2 的時候有看到有人說 Linux 底下玩 VR 軟體的部分只有 Index 比較適合而已，所以最近實際到手之後想要來試試看實際用起來的感覺。順便用用看最近大家滿推的新 Fedora...

軟體相容性包含幾個面向，這邊不廢話直接來測試一下...

## 測試一下

前置作業，我這邊把 Fedora 給裝起來
https://getfedora.org/en/workstation/download/

裝好之後這邊做一些前置作業，把環境搭起來

- dnf 設定調整一下 `sudo gnome-text-editor /etc/dnf/dnf.conf` 後面追加
```=bash
fastestmirror=True
deltarpm=True
max_parallel_downloads=10
```
- 系統更新 
```=bash
sudo dnf update
```
- 把 RPM-Fusion 裝起來，Free 跟 Non-Free 都要
```=bash
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```
- 把 FlatHub 裝起來
```=bash
sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

接下來就是一些軟體安裝的部分

- [安裝 NVidia 驅動](https://rpmfusion.org/Howto/NVIDIA)，最後一次重開後在登入畫面點又下的齒輪改成 Gnome (X.Org) 登入
```=bash
sudo dnf install akmod-nvidia -y
sudo dnf install xorg-x11-drv-nvidia-cuda
reboot
```
改成 X11 (X.Org) 登入其實滿重要的，[要不然到時候 Steam VR 會沒辦法正常抓取頭顯的訊號，並且報 307 的錯誤](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/355)。
- 安裝 Steam
```=bash
sudo dnf install steam
```

環境準備完成之後，把遊戲都抓下來吧
- 下載並安裝 SteamVR 跟 VRChat
- 在 Settings 的 Steam Play，勾選 Enable Steam Play for all other titles，底下確定使用的版本是 Photon Experimental

最後打開 SteamVR，設定完房間（視窗可能會當掉但一下子就恢復正常了），確定所有設備都有連好，頭顯內也有畫面，那就可以玩玩看了。

## 小小的細項與限制

基本上玩了一個多鐘頭沒遇到什麼難解之謎，跟朋友玩得滿開心的也能順暢的溝通

![可愛奇](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/VRChat_1920x1080_2022-08-28_22-28-27.536.png)

這邊列一些目前不會 Work 的東西
- Index 的 Camera 模式
- SteamVR Overlay 無法看見桌面（這個超級超級超級超級不方便）
- SteamVR Overlay UI 常常小故障，文字會不見這樣
- XSOverlay / OVR Toolkit 不會 Work
- Vive / Index 基站設定進不去（說是抓不到藍牙裝置但明明藍牙有開？，想要來調一下休眠設定）

一些比較不影響或是一些備註資訊
- SteamVR 的聲音控制自動切換是故障的，建議可以裝[這個 Tweak](https://extensions.gnome.org/extension/5135/audio-selector/)，在上設備之前先從右上方選單將輸出音效改為 HDMIx 頭顯，輸入音效改為 Valve Index HMD，下設備再改回來就好，然後 VRChat 那邊建議吃 Default。
- Video Player 按理來說要會 Work
- 效能上相較於 PC，幀率更爲不穩定，效能也比較差一點點，不過也還算可以接受的範圍
- EAC (Easy Anti Cheat) 不影響 VRChat 在 Linux 底下運作
- VRChat 的截圖被放在 `~/.steam/steam/steamapps/compatdata/438100/pfx/drive_c/users/steamuser/Pictures/VRChat`

目前就先這樣吧，想到什麼再補上來