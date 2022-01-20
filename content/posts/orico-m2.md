---
title: "開箱！Orico M.2 NVMe SSD 外接盒 (M2PV-C3) - 自己做個外接 SSD 吧！"
date: 2021-08-17T19:58:30+08:00
tags:
- 周邊
- 硬體
- 開箱
- 電腦
categories:
- 硬體
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

買了新的 MacBook 附帶的開箱 Part 3，應該是最後一篇了... 吧？

之前有說要解決掉 MacBook 笑死人的 256GB 容量的最佳解就是外接一個 SSD 來用，成本極低而且速度對於大部分的使用情境來說也夠了。

於是我的策略就是我手邊剛好有一顆 M.2 PCIe SSD，於是我就買個 dirty cheap 的四百塊外接盒來用，來看看這樣用起來如何。

話不多說，這邊就直接進入開箱

## 開箱

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/_DSF4877_S.JPG)

外盒，這個是標準版，NVMe 版本的。同樣外觀也有 NGFF 適用的，也有所謂「四倍散熱版」的東東，我是覺得就看預算吧，我這個扣一扣折扣大概三百六。

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/_DSF4878_S.JPG)

背後有寫詳細規格，大概如下：

- 型號：M2PV-C3
- 接口：USB 3.1 Gen2 Type-C
- 硬碟：M.2 MVMe
- 速度：10Gbps

要注意的一點是 M1 MacBook Air USB 速度上限就是 10Gbps（而且還很該死的跑不滿），你買了 20Gbps 的版本也沒用就是了。

硬碟選購上其實也不用硬攻頂，因為 10Gbps 的上限也才讀寫 1000MB 而已，在這個 SSD 隨便都破三千 MB 的年代這個確實很可笑。

至於 SATA SSD 值不值得考慮，目前我看的結果是選 SATA 沒有多少價格上的優勢，那這樣讀寫只有 500MB 我覺得不太划算。所以就不太建議省這個錢了。

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/_DSF4880_S.JPG)

盒裝配件，簡易說明、USB C 對 A 的線、USB C 對 C 的線、和小小配件包（包含螺絲、螺絲起子、導熱墊和SSD固定卡榫）

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/_DSF4882_S.JPG)

本體，還算洗練不是那麼廉價的外觀，散熱片是金屬，其餘都是塑膠殼。

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/_DSF4883_S.JPG)

USB-C 孔，插拔都滿緊的

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/_DSF4884_S.JPG)

拆開來有三個結構，散熱片、電路板、以及塑膠外殼

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/_DSF4885_S.JPG)

拿了手邊的 Intel 660p 512G，貼上包裝裡面附的導熱墊

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/_DSF4886_S.JPG)

確實安裝好就能將散熱片壓上去鎖起來

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/_DSF4887_S.JPG)

組合完成，應該那條線就會這樣一直插在上面了

## 速度小測

這邊以 Intel 660P 512G SSD 做個基礎，官方標示的速度為讀 1500 寫 1000

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-08-17%20115348.png)

首先就是看看硬碟在 Windows 底下的速度，雖然沒有跑剛剛好滿，但也是逼近了 USB 速度極限，讀 960 寫 925

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-08-17%20%E4%B8%8A%E5%8D%8811.58.57.png)

另外就是插在 M1 MacBook 底下，速度會打個折扣。讀 825 寫 700

這個速度問題算是一個 known issue，有人推測是 M1 給的頻寬造成的（雖然我覺得不太合理），不過不管再怎麼慢其實都比 SATA SSD 來得快，也能應付一些輕度剪輯，把程式放外面或是開發的需求。

## 結論

所以結論還是我不覺得花 6000 塊升級電腦的 SSD 到 500GB 很值得就是了，其實在 M1 MacBook Air 這樣的效能我寧願把這個錢投到 16GB 記憶體還比較實際。

而這個外接盒雖然才四百有找，但其實也提供了還算理想的體積，散熱以及速度，覺得還行啦！

不過還是要補充一點就是如果真的需要更好的速度，可能就要往 Thunderbolt 3 或是 USB 4 的 M.2 外接盒找了，同樣是 Orico 也有提供對應規格的產品，只是那個價格可以買快十個我這個外接盒，我覺得... 唉算了吧（苦笑）