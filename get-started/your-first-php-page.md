---
description: >-
  由於PHP可以完全寫在HTML裡面，因此很適合用來做為HTML的延伸，放一些經常重複寫到的原始碼、或者利用PHP從資料庫裡撈取資料以產生相應HTML原始碼等等。此時，我們所做的網頁便不再是需要一頁一頁寫好的靜態網頁，而成為一個可以動態載入資料的網頁，即所謂「動態網頁」。
---

# Your First PHP Page

PHP需要在合適的環境下才能執行使用，而最簡單的方法就是給他一個伺服器的環境。

## Environment

[XAMPP](https://www.apachefriends.org/zh_tw/index.html)提供了一個簡單的解決方案，讓你輕鬆在電腦上直接裝好Apache伺服器以及MySQL資料庫，一次搞定免去大量設定，裝好後我們就可以開啟伺服器來執行我們的PHP網站。

裝好後開啟XAMPP Control Panel，會出現在Windows右下角的小工具圖示，我們把Apache開啟按下Start。

![](../.gitbook/assets/xampp-control-panel.PNG)

開啟後如圖所示，我們還不需要用到MySQL資料庫，所以只要先開啟Apache伺服器就可以了。網站的預設根目錄會在`C:\xampp\htdocs`，如果你安裝XAMPP在其他地方，找到`htdoc`這個資料夾就是我們伺服器的根目錄。

打開瀏覽器，網址輸入`localhost`，XAMPP預設會跳轉至歡迎頁面`localhost/dashboard/`。

如果現在有看到「Welcome to XAMPP」的頁面，就代表伺服器架設成功，接下來就讓我們放入自己的PHP網頁吧。

## A PHP File

一個最簡單的PHP文件結構長這樣：

{% code-tabs %}
{% code-tabs-item title="index.php" %}
```php
<?php ?>
```
{% endcode-tabs-item %}
{% endcode-tabs %}



[http://www.twhappy.com/index.php?action=show&no=96](http://www.twhappy.com/index.php?action=show&no=96)

{% hint style="danger" %}
伺服器使用完畢之後，請務必回到XAMPP Control Panel將Apache按下Stop關閉。
{% endhint %}



