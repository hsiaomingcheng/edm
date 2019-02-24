---
tags: EDM,
disqus: hackmd
---

EDM電子報格式
===

###### tags: `EDM` `電子報` `電子信`

這幾天被電子報坑一個
決定把遇到的問題寫下來
改天還能回味

---

## 文字字型
我的想法是就用預設字型就好
我沒有實際去找出可不可以用的答案
不過～我有用引入線上字型試看看
是可以但是不保證每家的信箱都可以
``` HTML=
<link href="https://fonts.googleapis.com/css?family=Noto+Sans+TC" rel="stylesheet">
```


## css樣式
電子信的css最好是都寫在標籤上面
恩～因為你的格式 到各家的信箱上
class name會被替換掉所以就吃不到你的css樣式了
所以最好還是寫在標籤上面


## 格式
『 Table 』上網去google的結果普遍都會得到這個答案
大家都會説 要用table去切版
所以我也照著大家的說的去做 可惜我對table完全不熟
所以寫個結構就花很多時間
大概類似這樣

``` HTML=
<table align="center" border="0" cellpadding="0" cellspacing="0">
    <tr>
        <td>
            <table align="center" border="0" cellpadding="0" cellspacing="0">
                <!--信件title-->
                <tr>
                    <td>
                        <img src="http://logo.png" title="" alt="">
                    </td>
                </tr>
                <tr>
                    <td colspan="2">
                        <!--650x430-->
                        <img src="http://banner.jpg" alt="">
                        <p>信件主題</p>
                    </td>
                </tr>
                <tr>
                    <td colspan="2">
                        <h3>文章標題</h3>
                        <p>文字敘述</p>
                    </td>
                </tr>
                <tr valign="top">
                    <td>
                        <img src="http://aaa.jpg" alt="">
                        <p class="imgText">圖片短敘述</p>
                    </td>
                    <td>
                        <img src="http://bbb.jpg" alt="">
                        <p class="imgText">圖片短敘述</p>
                    </td>
                </tr>
            </table>
        </td>
    </tr>
</table>
 ```

↑↑↑↑↑↑↑↑↑↑↑↑
打完後在幾個不同信箱檢查過後很開心的給設計師看
設計師卻說 為什麼在手機看 文字跟圖片 這麼的小
能不能在手機上的時候放大
![](https://i.imgur.com/1NBnu5D.png)




## 重切 (div)
弄了很久還是不知道怎麼把 aaa 跟 bbb 這兩張在pc時候是併排
到手機上卻要變成一上一下然後照片滿版的樣式
我table的功力實在汗顏

後來發現其他人的廣告信
除了一開始用了個table > tr > td 之後全都是div
所以我也學著他做了一個

之後在手機上看就成功地把 aaa 跟 bbb 給分成一上一下且滿版
![](https://i.imgur.com/48Pwzq4.png)


``` HTML=
<style>
    @media (max-width: 420px) {
        .mailImgBox {
            display: table-row !important;
            text-align: center !important;
        }
    }
</style>
<div style="display: table; table-layout: fixed; width: 100%;">
    <div class="mailImgBox" style="padding-right: 2.5px; padding-bottom: 45px; width: 100%; display: table-cell;">
        <img src="http://aaa.jpg" style="width: 100%;" alt="">
        <div style="color: #9f9f9f; font-size: 14px; text-align: left; font-weight: 300;">圖片短敘述</div>
    </div>
    <div class="mailImgBox" style="padding-left: 2.5px; padding-bottom: 45px; width: 100%; display: table-cell;">
        <img src="http://bbb.jpg" style="width: 100%;" alt="">
        <div style="color: #9f9f9f; font-size: 14px; text-align: left; font-weight: 300;">圖片短敘述</div>
    </div>
</div>
```

---

以上就是我在做電子報遇到的一些問題
不一定全都是對的
有錯的地方 可以跟我說～
