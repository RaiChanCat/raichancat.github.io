---
title: "停損點抵達！ Openithm 初號機失敗紀錄"
date: 2021-06-27T19:17:55+08:00
tags:
- DIY
- Chunithm
- Openithm
- 手台
categories:
- 遊戲
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

這篇不是一篇教學，而是記錄一些內容好讓我一兩個月後能回來翻。

---

關於 Openithm 這玩意網路上的資訊頗少的，所以很多東西都只能頻經驗跟推測。當初就是看到有人兜出來一個寫好的韌體跟 3D 建模我就下去做了，做了之後才意識到這東西滿多 know-how，好像不是什麼短期就能一次搞定的東西短期就能一次搞定的東西。（雖然我做之前還天真地以為頻自己的技能能一次把所有東西都搞定）

反正我的紀錄就寫在這邊，希望有誰能看著堆屍體把東西做出來吧喵。

## 成本試算

- `JLCPCB` PCB 洗版 (包含10片主板 20片感測板)  $550
- `蝦皮` 外殼 -> 消耗掉一捲 PLA 耗材（含失敗）　$500
- `蝦皮` 客製壓克力切割 $540
- `蝦皮` Sparkfun Teensy LC $620
- `蝦皮` WS2812B LED 燈條 $189
- `電料行` 紅外線 LED 發射接收、排針、電阻、單芯線雜七雜八 $450
- `蝦皮中國` 74HC4051 模組 $38
- `蝦皮中國` 8P 30cm 排線 x10 $90
- `蝦皮中國` 3P 30cm 排線 x10 $60
- `蝦皮中國` 銅箔膠帶 0.05mm 30mm 30m $250
- `淘寶` 插針跟母座 $200
- `淘寶` 1/8W 精密電阻 $50
- `時間與心力` $無價

至少花了 ~3530，以及死掉的心 www

## 犯的錯誤

### 關於材料

其實最理想的狀況上面的材料如果一開始都從淘寶買，然後整批訂回來的造價成本可能可以少好幾百塊吧，台灣有很多東西因為是現貨的的關係所以造價會直接飛起來。

有一些購買的細節要注意：

- 插針、母座、1/8W電阻都是在台灣買不到東西，所以不用再浪費時間在光華商場一個一個翻。
- LED 燈條要注意有沒有滴膠，有滴膠的燈條是裝不上去的，另外 LED 應該是要另外供電才會亮起來。
- 蝦皮中國真的很慢很慢很慢很慢，我從淘寶買還比較快還比較便宜，唉。
- Teensy 有改版過，台灣有現貨的應該都是初代（v1.1 所需要的 code 有所不同，辨識方法是看電路板上有沒有寫版本號）
- PCB 洗版的經驗滿棒的，之前還傻傻的在台灣的拍賣看代洗 PCB 結果價格算出來都是天價，這種事情還是從中國那邊處理一次運回來就好。（雖然說 JLCPCB 是美金計價，不過看不出價格有多大的差異，也能直接上傳 gerber 檔）
- 買了便宜的電料行網路線要拿來做抬手台的延長線，結果一剝開來發現裡面他O的是多芯線... 考過乙檢然後做了無數條網路線的我，還真第一次知道原來多芯線有辦法做成網路線... 這完全不能用啊！！可想而知錫根本吃不上去直接滑走，最後只好整捆丟垃圾桶了...
- 按理來說排線應該要買 4P 而不是 3P...
- 壓克力的製作上規格是 3mm 厚度，472mm x 112mm 1片，103 mm x 26mm 16片  
  但是實際上切出來大片的偏長一點（因為最小單位是mm），可以考慮 471mm 之類的  
  另外為了考量到無套遊玩，其實霧面的壓克力板說不定也不錯？

### 關於製作

這很智障，因為我的東西不是一次到齊所以只能一個一個陸續組起來，結果很多時候組起來才發現自己完全搞砸了，但東西已經解焊不下來了...（私心覺得吸錫器不是個很好用的東西，然後吸錫線不知道怎麼搞的東西都吸不太起來，最後都直接當作焊上去是不可能拿起來的了。）

然後我居然把我的 Teensy 焊在上面了（扶額）  
結論就是不要像我一樣東西一到就迫不及待把東西弄起來，這簡直是災難...  
欣慰的一點就是沒有什麼太難焊之類的東西。

## 細節紀錄

### 所有的 Repo

jmontineri/OpeNITHM https://github.com/jmontineri/OpeNITHM  
最原始的 repo，基本上不用參考這個做，但是 Issue 裡面有不錯的組裝教學

veroxzik/OpeNITHM https://github.com/veroxzik/OpeNITHM/tree/teensy-32  
fork 出來的，裡面有針對韌體有做很多最佳化，以及 32 key 支援

skogaby/OpeNITHM https://github.com/jmontineri/OpeNITHM  
上面再 fork 出來的，裡面有鍵盤啟動自動校正的功能

nicoles/OpeNITHM https://github.com/nicoles/OpeNITHM  
上面再 fork 出來的，有講比較詳細的初始化設定以及微調

基本上彼此之間不太相容，所以如果要弄得話最好一次弄，不過電路之類的絕大部分都沒有差異

## 目前卡住的地方

- 刷好韌體接上電腦，紅外線會不停的傳送訊號，即使沒有接線也一樣
- 按鍵某種程度上會工作，但是刷了正確的韌體之後反而失效了
- LED 燈條不會 Work，看之前的敘述是

## 一些看有沒有機會補救的點

- Teensy 看有沒有機會拆起來
- 壓克力板應該也能沿用