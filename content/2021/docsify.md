---
title: "研究！用 Docsify 來代替 GitBook 寫文件吧"
date: 2021-07-18T11:36:08+08:00
tags:
- 開發
- Docsify
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

![](https://raw.githubusercontent.com/raichancat/raichancat.github.io-images/master/img/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202021-07-18%20114330.png)

## 簡介

首先不免俗地來簡單介紹一下 Docsify 是什麼。
Docsify 是一個文件生產器，以線上直接解析 Markdown 的方式來呈現網頁內容。

特色：

- 無靜態產生的 HTML 檔（除了首頁的設定檔 HTML 以外其他都是 MD 檔）
- 簡單而且輕量
- 內建搜尋外掛
- 多種佈景
- 外掛支援
- 表情符號支援
- IE11 支援
- 支援伺服器端 render

簡單來說就是一個好用的文件生產器，快速產生一個類似 GitBook  架構的網站，能掛在任何伺服器或是 GitHub Pages 之類的地方。

## 安裝

1. 先確定電腦有裝 [NPM](https://www.npmjs.com/) 吧，沒有的話去裝一下。
2. 打開要存放的位置，用命令提示字元開啟這個路徑
(有裝 Windows Terminal 的話右鍵就有了，要不然就用 `cd {路徑}` 吧)
3. 安裝 Docsify 至全系統
```bash
npm i docsify-cli -g
```

## 建立檔案
假設我們要將文件存放於 docs 資料夾裡面，我們就輸入指令
(至於為什麼是 docs，其實是為了 GitHub Pages 的預設目錄，能夠輕鬆地掛起來。)
```bash
docsify init ./docs
```

這邊解釋一下裏頭的文件分別在幹嘛
- `index.html` 進入的網頁，也是所有設定設定的地方
- `README.md` 首頁的內容
- `.nojekyll` 避免 GitHub Pages 當成這是個 Jekyll 忽略部分檔案的標記

---

文件的部分就是直接用 Typora 或是 VSCode 之類的工具編輯 md 檔即可，基本上絕大部分的語法都是無痛支援的，也能夠直接吃先前 GitBook 出來的檔案，其實我覺得很棒。

如果你沒有寫過 MD 檔或是沒有概念的話，這邊附上兩個參考：
[寫作＆筆記神器 MarkDown 真希望我學生時期就懂！](https://medium.com/@mdzeng/%E5%AF%AB%E4%BD%9C-%E7%AD%86%E8%A8%98%E7%A5%9E%E5%99%A8markdown-%E7%9C%9F%E5%B8%8C%E6%9C%9B%E6%88%91%E5%AD%B8%E7%94%9F%E6%99%82%E6%9C%9F%E5%B0%B1%E6%87%82-26becb160f6e)
[Typora](https://typora.io/)

## 預覽

建立一個虛擬的伺服器能即時的預覽撰寫好的 docsify 檔案
```bash
docsify serve docs
```
預設的 IP 位址會是 http://localhost:3000

## 部屬

把剛剛建立的專案檔資料夾內容丟到網頁伺服器就能用了。

---

對，你沒看錯，就是這麼簡單吧。基本上只要掌握上面四點就能寫出一份完整的文件。
接下來的部分就是屬於進階的部分了，像是多文件並排，布景以及外掛一類的，讓自己的文件更棒。

## 進階使用

### 設定檔

設定檔是 `index.html`，設定的參數多擺在底下有個 script 的欄位，然後把外掛網址以相同型式貼在底下

```html
<!-- docs/index.html -->

<script>
	<!-- 外掛參數1 -->,
     <!-- 外掛參數2 -->, 
</script>
<script src="<!-- 外掛1網址 -->"></script>
<script src="<!-- 外掛2網址 -->"></script>
```

### 側邊攔

文件寫多了需要在左手邊進行分類，首先先確定 loadSidebar: true

```html
<script>
  window.$docsify = {
    loadSidebar: true
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```

在檔案夾底下建立 `_sidebar.md`
格式是 `* [選單標題](/[路徑] "[頁面標題]")`

如果指定的是資料夾，則是讀取底下的 `ReadMe.md`，如果指定的是 MD 檔，則是 MD 檔本身

```markdown
<!-- docs/_sidebar.md -->

* [主頁面](/ "頁面標題")
* [文件1](page1.md "頁面標題")
* [文件2](page1.md "頁面標題")
```

如果要分層，則是建立一個資料夾把檔案塞進去，再建一個 `_sidebar.md`
這樣當你點到主頁面的標籤以後就會展開來 3 跟 4

```markdown
<!-- docs/pages/_sidebar.md -->

* [主頁面](/ "頁面標題")
	* [ - 文件3](/pages/page1.md "頁面標題")
	* [ - 文件4](/pages/page1.md "頁面標題")
* [文件1](page1.md "頁面標題")
* [文件2](page1.md "頁面標題")
```

### 文件目錄

[justintien/docsify-plugin-toc](https://github.com/justintien/docsify-plugin-toc)

預設是沒有文件目錄的，如果需要可以讓它顯示在右手邊

```html
<!-- docs/index.html -->

<script>
    window.$docsify = {
      toc: {
        tocMaxLevel: 5,				<!-- 最多層 -->
        target: 'h2, h3, h4, h5, h6' <!-- 以標題幾為標題 -->
      },
    }
</script>
<script src="//unpkg.com/docsify-plugin-toc"></script>
```

### 語法突顯

Docsify 預設有支援這些語言，無須外掛

- Markup - `markup`, `html`, `xml`, `svg`, `mathml`, `ssml`, `atom`, `rss`
- CSS - `css`
- C-like - `clike`
- JavaScript - `javascript`, `js`

如果不在上面的語言需要手動添加，程式語言名稱可以看 [這邊](https://prismjs.com/#supported-languages)  
格式如 `<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-[程式語言].min.js"></script>`

```html
<!-- docs/index.html -->

<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-python.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-csharp.min.js"></script>
```

在撰寫的時候只要程式碼框有註記語言就能使用

```markdown
​```python
print("Hello World")
​```
```

### 提示框框

[fzankl/docsify-plugin-flexible-alerts](https://github.com/fzankl/docsify-plugin-flexible-alerts)

![](https://user-images.githubusercontent.com/44210522/93708131-10fb5780-fb34-11ea-85ae-e18b3e239f83.jpg)

設定如下

```html
<!-- docs/index.html -->

<script>
  window.$docsify = {
    'flexible-alerts': {
      style: 'flat'	      <!-- 佈景，flat 為右邊 callout 為左邊 -->
      note: {
        label: "註記"		<!-- 名稱 -->
      },
      tip: {
        label: "技巧"		<!-- 名稱 -->
      },
      warning: {
        label: "警告"		<!-- 名稱 -->
      },
      attention: {
        label: "注意"		<!-- 名稱 -->
      }
    }
  };
</script>
<script src="https://unpkg.com/docsify-plugin-flexible-alerts"></script>
```

在撰寫普通的 Markdown 文件的時候可以這樣引用

```markdown
> [!NOTE]
> 這是個註記

> [!TIP]
> 這是個技巧

> [!WARNING]
> 這是個警告

> [!ATTENTION]
> 這是個注意
```

###  圖片點一下縮放

無須參數，設定如下

```html
<!-- docs/index.html -->

<script src="//unpkg.com/docsify/lib/plugins/zoom-image.min.js"></script>
```

### 程式框複製按鈕

無須參數，設定如下

```html
<!-- docs/index.html -->

<script src="//unpkg.com/docsify-copy-code"></script>
```

### 頁面滾回頂部按鈕

[zhengxiangqi/docsify-scroll-to-top](https://github.com/zhengxiangqi/docsify-scroll-to-top)

設定如下

```html
<script>
    window.$docsify = {
        // ...
        scrollToTop: {
            auto: true,
            text: 'Top',	<!-- 文字顯示 -->
            right: 15,		<!-- 方位右邊 -->
            bottom: 15,		<!-- 方位下面 -->
            offset: 500
        }
    };
</script>
<script src="//unpkg.com/docsify-scroll-to-top/dist/docsify-scroll-to-top.min.js"></script>
```