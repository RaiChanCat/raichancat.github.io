---
title: "研究！Google 表單透過網址一鍵自動填寫表單內容！"
date: 2021-07-31T14:36:17+08:00
tags:
- Google
- 網路
- 軟體
- 開發
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

## 原理

透過網址來預填表單，格式如下

https://docs.google.com/forms/d/e/viewform?**[表單連結]**&**[欄位1代號]**=**[欄位1內容]**&&**[欄位2代號]**=**[欄位2內容]**...

- 表單連結點進去就會自動填入所有的項目
- 項目可以跨頁
- 跨頁的下一步還是得自己按
- 不管是選擇，簡答，下拉式選單，欄位內容的部分就直接填寫文字內容（或是選擇的內容）即可

## 欄位代號取得

1. 打開表單，點擊 `F12` 開啟開發人員面板
   ![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-07-31%20%E4%B8%8B%E5%8D%882.54.32.png)
2. 在面板按下 `command`+`F` 或是 `control` + `F` 搜尋元素，輸入 `entry.`
   ![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-07-31%20%E4%B8%8B%E5%8D%882.55.05.png)
3. 你可以看到
   action="" 欄是表單連結
   name="entry.xxxxxxxxxx" 是欄位代號
   value="aaaa" 是欄位內容
   ![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-07-31%20%E4%B8%8B%E5%8D%882.54.53.png)

## 網址建立

複製一下網址的連結，按照上面按照 [原理](#原理) 給的格式貼入相關的元素，拿我這份表單舉例

https://docs.google.com/forms/d/e/viewform?**[表單連結]**&**[欄位1代號]**=**[欄位1內容]**&&**[欄位2代號]**=**[欄位2內容]**...

```
https://docs.google.com/forms/d/e/1FAIpQLSfN7WG27WOFUKygeLOPAMmI5N8TpsZH1hQENMGSAcGil7AGyQ/viewform?entry.1876558801=110/07/31&entry.1136496505=0900000000&entry.437250203=37.5&entry.836727167=A班&entry.1919260157=男&entry.1695249575=aaaa
```

順序其實無所謂，填完之後開新分頁打開連結

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E6%88%AA%E5%9C%96%202021-07-31%20%E4%B8%8B%E5%8D%883.07.21.png)

將將！東西都自動填完了

## 延伸應用

基本上有了網址之後很多事情就好辦了。

舉個例子就是如果你要用在「捷徑」App 的話，只要在捷徑裡面撰寫程式碼，呼叫 Safari 開啟即可。
例如說我其中一個欄位想要產生在 36.5~37.5 之間的亂數，以變數的方式安插在 URL 裡面就可以了
或者是如果要分享給親朋好友用，透過 回報 的指令把一些欄位挖空即可，玩法還很多呢 www

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/IMG_08456.PNG)

作完之後不免俗的放到桌面上方便之後快速呼叫多舒服www

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/photo_2021-07-31%2015.30.03.jpeg)

---

除此之外像是剛剛有取出的 action 連結甚至可以拿來當作 POST 來用，可以直接傳參數進去做到完全自動化的填表單，酷吧！