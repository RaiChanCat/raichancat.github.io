---
title: "HoloLens - MRTK 如何打包 AppX 安裝檔"
date: 2021-07-14T10:39:36+08:00
tags:
- HoloLens 2
- Unity
- MRTK
- 開發
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

Unity 版本：2020.3.13  
MRTK 版本：2.7.2

## 準備

在開始之前確保自己的 MRTK 專案有安裝「Mixed Reality Toolkit Tools」包，使用裡面的工具比較懶人方便。

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-12%20175244.png)

## 流程

打開 Mixed Reality > Utilities > Build Window 開啟編譯視窗

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-12%20175711.png)

檢查 Scene 已經加入了上方 Scene in Build 視窗當中  
Target Device 選擇 HoloLens  
點擊 Build Unity Project。

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-12%20181452.png)

編譯的檔案會被放置於 `/專案資料夾/Builds/WSAPlayer`
編譯完成會顯示 Build Complete 視窗，點擊 Build AppX

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-12%20181654.png)

編譯途中不會有任何視窗，內容都會顯示於 Console 當中。完成之後會顯示 Command Successful

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-12%20182209.png)

編譯完成的執行檔會放置於 `/專案資料夾/Builds/WSAPlayer/AppPackages/執行檔名稱/完整執行檔名稱` 底下

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-13%20115039.png)

## 檔案架構

- `.appx` 軟體安裝檔
- `Dependencies` 依賴
    - `ARM64` ARM64 平台依賴
        - `.appx` 依賴安裝檔

安裝的時候需要同時安裝軟體本體的 AppX 以及依賴的 AppX
其他的檔案就不是那麼重要了。