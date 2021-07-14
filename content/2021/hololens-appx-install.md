---
title: "HoloLens - MRTK 如何安裝 AppX 安裝檔"
date: 2021-07-14T11:01:00+08:00
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

```
透過這種方法，安裝前須先將舊版軟體解除安裝
```

## 準備

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-13%20115039.png)

將編好的 Appx 準備好，並且將 HoloLens 與電腦連接同一個 WiFi (網路) 底下。（你可以從 HoloLens 的 WiFi 設定檢查你的 IP）

## Windows 裝置入口網站

```
若已設定過可以跳過
```

HoloLens 到 設定 > 更新與安全性 > 開發人員專用 底下開啟 裝置入口網站

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/20210713_111521_HoloLens.jpg)

電腦打開瀏覽器，輸入 HoloLens 上給的的 IP 位址，接受風險並繼續

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-13%20112036.png)

點擊 Request pin 的按鈕

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-13%20112146.png)

此時 HoloLens 上會顯示 pin 碼

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/20210713_112355_HoloLens.jpg)

將資料輸入到瀏覽器當中
- **PIN displayed on your device** 頭顯顯示的 PIN 碼
- **New user name** 使用者名稱
- **New password** 密碼
- **Confirm password** 重新輸入密碼

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-13%20112435.png)

瀏覽器會提示登入，輸入剛剛設定好的資訊

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-13%20112500.png)

Windows 裝置入口網站順利開啟

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/Inked%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-13%20112516_LI.jpg)

## AppX 安裝

執行檔的結構如下

- `.appx` 軟體安裝檔
- `Dependencies` 依賴
    - `ARM64` ARM64 平台依賴
        - `.appx` 依賴安裝檔

安裝時我們需要軟體安裝檔，以及依賴安裝檔(可能有很多個)  
打開 Views > Apps 就能夠看到應用程式介面

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-13%20113349.png)

在上方 Deploy apps 裡面點選 瀏覽 開啟 軟體安裝檔(.appx)  
若有依賴安裝檔，請勾選 Allow me to select framework packages，點擊 Next 繼續

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-13%20115640.png)

再次點選 瀏覽，開啟 依賴安裝檔(.appx)。全數加入完畢後按 Install

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-13%20113923.png)

當顯示 Package Successfully Registered 即安裝完畢

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-13%20120709.png)