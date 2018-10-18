# Make Webpages Online

## VPS & Domain

上一個章節我們在電腦上安裝了XAMPP來架設一個本機伺服器，不過在實務上我們也很常會購買虛擬主機（VPS）的服務，用來作為我們自己的網站的伺服器。一來效能經過調教、二來也相對穩定較不會斷線。

虛擬主機上的伺服器環境安裝好後，通常會得到一個IP位址，透過這個IP我們的網站就可以讓其他人來連線。但IP四個數字並不是很好記，所以通常會在指派一個網域（Domain）給伺服器，經過設定過後伺服器就會知道，該網域應該要對應到哪個資料夾作為根目錄。

假設一切安裝妥當，並且我們得到一組帳號密碼可以利用FTP來登入伺服器，那就可以來試著把之前做好的網頁都上傳上伺服器看看吧！

可以安裝[FileZilla Client](https://filezilla-project.org/)這個軟體來完成上傳、下載等任務，如果想要含SSH功能也很推薦[MobaXterm](https://mobaxterm.mobatek.net/)安裝這個軟體。

{% hint style="info" %}
要使用SFTP連線的話，Port要設定為22，或者在IP前面加上`sftp://`。
{% endhint %}

## Server Root & Domain Root

伺服器連上之後，預設會進入自己的主目錄可能是類似`/home/username`，至於網域的根目錄則通常會是在`public_html`資料夾內，例如你的伺服器上的資料夾樹狀圖可能如下所示。

```text
/home/username/
├── etc/
├── log/
├── mail/
├── public_ftp/
├── public_html/
│	├── index.php
│	├── css/
│	│   ├── bootstrap.min.css
│	│   └── main.css
│	├── js/
│	│   ├── jquery.min.js
│	│   └── main.js
│	└── test/
│	    ├── index.php
│	    ├── todolist.html
│	    ├── css/
│		│   ├── bootstrap.min.css
│		│   └── main.css
│		└── js/
│		    ├── jquery.min.js
│		    └── main.js
├── ssl/
└── tmp/
```

我們必須要把網頁的檔案全部都放在`public_html`這個目錄底下，這樣在指定的網域下才能夠抓得到檔案。

假設有一個網域`www.foo.com`現在指向這個伺服器的IP，我們就可以在瀏覽器上輸入`www.foo.com`來訪問到伺服器上，網域後面不指定檔案名稱的話預設會去抓`index.html`或是`index.php`，所以就會是`/home/username/public_html/index.php`這個檔案。

{% hint style="success" %}
使用者在網路上輸入的網址：www.foo.com  
伺服器上的路徑及檔案名稱：/home/username/public\_html/index.php
{% endhint %}

當然，透過這樣的結構，我們可以陸續透過不同的網址來訪問到`public_html`這個目錄底下的所有其他檔案，例如我們進入`www.foo.com/test`，這樣就變成會看到`test`資料夾底下的`index.php`。其他檔案例如`www.foo.com/test/todolist.html`等等以此類推。  


