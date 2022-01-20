---
title: "研究！Windows 10 VHD 虛擬硬碟安裝大法"
date: 2021-06-29T22:42:49+08:00
tags:
- Windows
categories:
- 作業系統
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
    hidden: true # only hide on current single pag
---

這篇是面向有自行安裝 Windows 經驗的使用者，安裝的部分會直接略過。

---

原本是想說來寫一篇文章講 Windows 11 裝進 VHD 測試，不過裝到一半才發現 VHD 的安裝方式不適用 10 升級 11，所以就只留下了安裝的前半段，就當作某種紀錄寫起來吧。

以前小時候有看過把 Windows 7 裝在 VHD 的大法，過了這麼多年我還是第一次實作在現在的系統上，而且意外的滿檢的 www。雖然絕大多數的使用者不應該採用這種安裝方式，但其實某種層面上還是有些時候還不錯用，尤其是在要維護一堆電腦的環境。

## 誰需要這樣裝?

- 想要能快速部屬大量電腦的人，把 Windows 裝在 VHD 裡面可以快速 copy 到每一台電腦直接開機。
- 當作系統還原使用，當系統掛掉直接複製貼上 VHD 回來開機繼續用。

## 安裝

### 事前準備

- [Windows 10 ISO ](https://www.microsoft.com/zh-tw/software-download/windows10)  
Tips: 打開後瀏覽器按 F12 開啟開發者模式，裡面有個手機圖案按下去就會以手機畫面顯示，切換上面的手機可以模擬硬體，按重新整理之後就能直接以原始連接的方式下載 ISO 檔
- [Rufus](https://rufus.ie/zh_TW/)，然後把 ISO 做成安裝隨身碟，這部分因為是常識我就不再贅述
- 幾個鐘頭的時間

### 進到 Windows 安裝

1. 開機進 Boot Menu，選擇隨身碟開機  
    （華碩筆電 `Esc`、華碩桌機 `F8`，其他品牌桌機 `F12` 之類的）
2. 開機進到安裝視窗（選擇語言），`Shift`+`F10` 啟動命令提示字元

### 硬碟抓取並指定磁碟機代號

3. 輸入指令，進入 Diskpart
```
diskpart
```
4. 輸入指令，列出所有的硬碟，磁碟機會以 0123 表示
```
list lisk
```
5. 假設是磁碟 0，輸入指令 `select disk [硬碟數字]`，選擇磁碟 0
```
select disk 0
```

6. 輸入指令，剛剛選擇的硬碟裡面所有的分割區
```
list partition
```
7. 在裏頭尋找，通常會有個「主要」標籤的分割區，  
    通常就是 C 槽本身，像我是分割區2，輸入 `select partition [分割區數字]`，選擇分割區 2
```
select partition 2
```
8. 指定磁碟區，假設是要指定為 W槽，輸入 `assign letter=[磁碟機代號]`
```
assign letter=w
```
9. 成功後，Diskpart 會提示成功訊息，輸入指令離開 Diskpart
```
exit
```

### 建立虛擬硬碟

10. 在剛剛指定的磁區底下，我們建立一個資料夾叫做 `vdisk` 放我們的 VHD
```
mkdir w:\vdisk
```
11. 輸入指令，再次進入到 Diskpart
```
diskpart
```
12. 輸入指令，在 W 槽裡面的 vdisk 資料夾建立 VHD，設定硬碟大小為 128GB，設定為可擴充性的 
`create vdisk file=”[檔案位置]” maximum=[硬碟大小 MB] type=[VHD 模式]`
```
create vdisk file=”w:\vdisk\windows10.vhdx” maximum=131072 type=expandable
```
13. 輸入指令，將剛剛建立的 VHD 掛載到系統當中（讓目前的安裝程式能夠看得到這顆硬碟）
```
attach vdisk
```
14. 提示成功訊息之後，關閉視窗開始安裝 Windows，自訂安裝並選擇硬碟到一個新出現的未配置空間即可。