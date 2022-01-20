---
title: "研究！Unreal Engine 4 Dump 遊戲素材"
date: 2021-06-25T23:21:30+08:00
tags: 
- 遊戲
- 開發
- Unreal
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

不要拿來做一些奇怪的事，OK？

## 拆包的一些基本常識

- UE4 的素材裝在遊戲目錄底下的 `Content/Paks` 裡面的 Pak 檔，檔名上面會註明平台 `-WindowsNoEditor` 或是 `-AndroidASTC` 之類的
- UE4 的執行檔放在 `Binaries` 裡面，像 Windows 會存放在 `Binaries\Win64` 裡面，通常檔名會帶有 `-Win64-Shipping.exe` 

### 簡易的流程

1. 絕大多數的 UE4 遊戲會將 pak 加密，因此我們要從遊戲運行當中擷取 AES 的金鑰。
2. 透過專門的解包的工具將東西取出
3. 透過能讀取 uassets 的工具來檢視裡面的內容

## 流程

### AES 金鑰尋找

1. 準備好 pak 檔案以及遊戲 exe 執行檔
2. 下載 [AES Key Finder 1.9](https://zenhax.com/viewtopic.php?t=9407&start=20) 解壓縮
3. 將遊戲 exe 執行檔貼到解壓縮後的 AES Key Finder 資料夾底下
4. 將遊戲執行檔 exe 拖到 RUN Find 256-bit UE4 AES Key.bat，按 Enter 繼續![](https://i.imgur.com/hqVOyub.jpg)

5. 會做一些基本檢查，一路按  Enter 繼續
   ![](https://i.imgur.com/7olynqd.jpg)

6. 當找到金鑰的時候會顯示 Possible AES Key found! 複製起來備用，此時程式仍然會繼續尋找其他的
   ![](https://i.imgur.com/MOp9ber.jpg)

7. 最終找完了就沒有後續了，任意鍵關閉視窗即可
   ![](https://i.imgur.com/H4N7cIj.jpg)
8. 金鑰轉換，將剛剛的 key 貼進 `key.txt`，跑 `RUN Convert key.txt to base64.bat` 輸出的 key 會在 base64key.txt

### 解包

1. 下載 [quickbms](http://aluigi.altervista.org/papers/quickbms.zip) 並解壓縮
2. 下載 [unreal_tournament_4.bms](https://zenhax.com/viewtopic.php?f=9&t=1005) 並將檔案放在 quickbms 底下
3. 雙擊點開 quickbms_4gb_files.exe
4. 跳出開啟檔案視窗，選擇剛剛下載的 unreal_tournament.bms 腳本
5. 跳出第二次開啟檔案視窗，選擇你的 pak 素材包檔案
6. 跳出第三次開啟檔案視窗，選擇你解包後的位置
7. 若此 pak 包無加密，就會進入到解包的程序，若有加密請在這個步驟貼上剛剛的金鑰再 Enter 解包
   ![](https://i.imgur.com/6T4gTrO.png)

8. 你可以在你的輸出目錄看到你解包後的檔案，你就能用 UModel 之類的檢視器查看內部的檔案