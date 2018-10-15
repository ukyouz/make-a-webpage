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

開啟後如圖所示，我們還不需要用到MySQL資料庫，所以只要先開啟Apache伺服器就可以了。網站的預設根目錄會在`C:\xampp\htdocs`，如果你安裝XAMPP在其他地方，找到`htdoc`這個資料夾就是我們伺服器的預設根目錄，也就是`localhost`這個位址將會實際抓到的本機目錄。

{% hint style="info" %}
如果想要`localhost`的根目錄是在其他資料夾，需要進入伺服器設定檔`httpd.conf`修改，較為麻煩，請先保持預設。
{% endhint %}

現在打開瀏覽器，網址輸入~~`localhost`~~，XAMPP預設會跳轉至歡迎頁面`localhost/dashboard/`。如果有看到「Welcome to XAMPP」的頁面，就代表伺服器架設成功，接下來就讓我們放入自己的PHP網頁吧。

## A PHP File

一個最簡單的PHP文件結構長這樣：

{% code-tabs %}
{% code-tabs-item title="index.php" %}
```php
<?php ?>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

欸，沒東西。是的，`<?php ?>`只是我們用來告訴伺服器說要執行PHP程式碼的地方，現在讓我們加入一點程式碼。

{% code-tabs %}
{% code-tabs-item title="index.php" %}
```php
<?php
    echo 'Your first PHP webpage!!';
?>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

把這個內容存檔為`index.php`取代掉原本放在`C:\xampp\htdocs`資料夾裡預設的`index.php`，瀏覽器網址輸入`localhost`，現在你會看到頁面顯示。

```text
Your first PHP webpage!!
```

伺服器會預設在根目錄下讀取以`index`命名的檔案，例如：`index.html`或`index.php`，所以在瀏覽器網址輸入`localhost`，伺服器就會去找到`localhost/index.php`這個檔案，而這個檔案在電腦裡的實際位置，就是`C:\xampp\htdocs\index.php`。

{% hint style="info" %}
如果不想要覆蓋掉原本的檔案，就先把原有的`index.php`重新命名吧。
{% endhint %}

更多關於PHP的語法，可以參考[TwHappy部落格網誌](http://www.twhappy.com/index.php?action=show&no=96)，我們這邊要來談談PHP與HTML愛恨情仇的合作關係。

## HTML In PHP

在開始這節之前，我們先把前面用來放網頁的資料夾`web_abc`複製到預設根目錄`C:\xampp\htdocs`裡面，然後把以下內容存為`index.php`放在根目錄。

一個PHP檔案裡面可以直接寫入HTML原始碼，你只要把HTML原始碼寫在`<?php ?>`的範圍之外效用等同於一般HTML網頁，甚至一個PHP檔案裡可以不包含任何PHP程式，只拿來寫HTML也可以。

{% code-tabs %}
{% code-tabs-item title="index.php" %}
```php
<html>
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style></style>
</head>
<body>
	<nav>
		<a href="/">Home Page</a>
		<a href="/web_abc/resume.html">Resume</a>
		<a href="/web_abc/biography.html">Biogragphy</a>
	</nav>
	<h1>It Works!</h1>
</body>
</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

請留意，現在的副檔名是`.php`，所以必須在伺服器環境下才能執行看到，但文件內容看起來就就只是一般的HTML網頁。那我們現在來放點PHP程式碼，可以放在任何位置，只要記得務必要用`<?php ?>`把程式碼包起來。

{% code-tabs %}
{% code-tabs-item title="index.php" %}
```php
<html>
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style></style>
</head>
<body>
	<nav>
		<a href="/">Home Page</a>
		<a href="/web_abc/resume.html">Resume</a>
		<a href="/web_abc/biography.html">Biogragphy</a>
	</nav>
	<h1>It Works!</h1>
	<?php
	    echo '<p>Your first PHP webpage!!</p>';
	?>
</body>
</html>
```
{% endcode-tabs-item %}

{% code-tabs-item title="In browser" %}
```markup
<html>
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style></style>
</head>
<body>
	<nav>
		<a href="/">Home Page</a>
		<a href="/web_abc/resume.html">Resume</a>
		<a href="/web_abc/biography.html">Biogragphy</a>
	</nav>
	<h1>It Works!</h1>
	<p>Your first PHP webpage!!</p>
</body>
</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

瀏覽器網址輸入`localhost`並重新整理，現在你就可以看到一個由PHP產生的網頁，按下「滑鼠右鍵、檢視網頁原始碼」，你就可以看到PHP執行後所動態產生的HTML網頁檔案。

這有甚麼用呢？用途可多了。

### Include PHP Files

例如我們可以在PHP網頁中引入另一個PHP檔案，這尤其好用在網頁有共同部分的時候，像我們就可以把網頁中的導覽列之前的HTML原始碼整個切出來，存成一個檔案來讓所有網頁共用。

{% code-tabs %}
{% code-tabs-item title="index.php" %}
```php
<?php
	include 'header.php';
?>
	<h1>It Works!</h1>
	<?php
	    echo '<p>Your first PHP webpage!!</p>';
	?>
</body>
</html>
```
{% endcode-tabs-item %}

{% code-tabs-item title="header.php" %}
```php
<html>
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style></style>
</head>
<body>
	<nav>
		<a href="/">Home Page</a>
		<a href="/web_abc/resume.html">Resume</a>
		<a href="/web_abc/biography.html">Biogragphy</a>
	</nav>
```
{% endcode-tabs-item %}

{% code-tabs-item title="In browser" %}
```markup
<html>
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style></style>
</head>
<body>
	<nav>
		<a href="/">Home Page</a>
		<a href="/web_abc/resume.html">Resume</a>
		<a href="/web_abc/biography.html">Biogragphy</a>
	</nav>
	<h1>It Works!</h1>
	<p>Your first PHP webpage!!</p>
</body>
</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

仔細瀏覽上面範例中的`index.php`及`header.php`兩個檔案，你可在`In browser`頁籤中看到使用者將會看到的網頁內容。其原理就是`include`會把整份`header.php`檔案貼到`index.php`裡面，這甚至包含變數都可以一起被使用。

例如我們在頁面`index.php`中設定一個PHP的變數`$page`為`Home`字串，則用來引入的`header.php`也可以讀到這個變數的值，進一步拿來使用，例如改變網頁標題、或者用來判斷當前的頁面。

底下的例子將變數`$page`用來設定當前頁面標題名稱，並且顯示在內文段落中。請留意`header.php`中要使用PHP程式碼的部分，一定要記得用`<?php ?>`包起來。

{% code-tabs %}
{% code-tabs-item title="index.php" %}
```php
<?php
	$page = 'Home';
	include 'header.php';
?>
	<h1>It Works!</h1>
	<?php
	    echo '<p>Your first PHP webpage: '.$page.'!!</p>';
	?>
</body>
</html>
```
{% endcode-tabs-item %}

{% code-tabs-item title="header.php" %}
```php
<html>
<head>
	<meta charset="UTF-8">
	<title><?php echo $page; ?></title>
	<style></style>
</head>
<body>
	<nav>
		<a href="/">Home Page</a>
		<a href="/web_abc/resume.html">Resume</a>
		<a href="/web_abc/biography.html">Biogragphy</a>
	</nav>
```
{% endcode-tabs-item %}

{% code-tabs-item title="In browser" %}
```markup
<html>
<head>
	<meta charset="UTF-8">
	<title>Home</title>
	<style></style>
</head>
<body>
	<nav>
		<a href="/">Home Page</a>
		<a href="/web_abc/resume.html">Resume</a>
		<a href="/web_abc/biography.html">Biogragphy</a>
	</nav>
	<h1>It Works!</h1>
	<p>Your first PHP webpage: Home!!</p>
</body>
</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### HTML Inside PHP Statement

我們甚至可以加一點判斷條件，讓頁面上不要顯示連到自己的連結，例如我們在`header.php`裡面動一點手腳，增加一個`if`判斷式。例如：

{% code-tabs %}
{% code-tabs-item title="index.php" %}
```php
<?php
	$page = 'Home';
	include 'header.php';
?>
	<h1>It Works!</h1>
	<?php
	    echo '<p>Your first PHP webpage: '.$page.'!!</p>';
	?>
</body>
</html>
```
{% endcode-tabs-item %}

{% code-tabs-item title="header.php" %}
```php
<html>
<head>
	<meta charset="UTF-8">
	<title><?php echo $page; ?></title>
	<style></style>
</head>
<body>
	<nav>
		<?php if ($page!='Home') { ?><a href="/">Home Page</a><?php }; ?>
		<a href="/web_abc/resume.html">Resume</a>
		<a href="/web_abc/biography.html">Biogragphy</a>
	</nav>
```
{% endcode-tabs-item %}

{% code-tabs-item title="In browser" %}
```markup
<html>
<head>
	<meta charset="UTF-8">
	<title>Home</title>
	<style></style>
</head>
<body>
	<nav>
		
		<a href="/web_abc/resume.html">Resume</a>
		<a href="/web_abc/biography.html">Biogragphy</a>
	</nav>
	<h1>It Works!</h1>
	<p>Your first PHP webpage: Home!!</p>
</body>
</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

最奇特的地方，就是大括號的左邊`{`跟右邊`}`是可以散佈在不同的`<?php ?>`裡面的，只要在同一個檔案，PHP程式就能夠理解。從`In browser`頁籤中，我們可以發現到PHP如何讓一個連結不顯示。當然你要寫在一起也是可以的，只是HTML的部分就要變成是一個字串，例如以下示範的兩行程式是等效的。

```php
<?php if ($page!='Home') { ?><a href="/">Home Page</a><?php }; ?>
<?php if ($page!='Home') { echo '<a href="/">Home Page</a>'; }; ?>
```

另外還有一種寫法，是使用`if`與`endif`，效果也都是一樣的。

```php
<?php if ($page!='Home') : ?><a href="/">Home Page</a><?php endif; ?>
<?php if ($page!='Home') : echo '<a href="/">Home Page</a>'; endif; ?>
```

如果你遇到了這個錯誤：

**Notice**: Undefined variable: page in **C:\xampp\htdocs\index.php** on line **\#\#**

表示你沒有正確引入一些檔案，或者在`index.php`檔案中，你還沒有定義一個`$page`變數，或者你打錯字（笑。

### 動手時間

現在，讓我們把前面做好的網頁都改成PHP吧，然後就可以分別引入我們寫好的`header.php`檔案，接著只要為每個頁面設定好`$page`這個PHP變數，就可以一次把導覽列做好啦！

{% hint style="info" %}
只要我們需要在網頁中使用PHP程式碼，就需要把`.html`副檔名改為`.php`。另外，一定要在有安裝PHP的伺服器環境中。
{% endhint %}

例如你可能最後會做出這樣的`header.php`。

{% code-tabs %}
{% code-tabs-item title="header.php" %}
```php
<html>
<head>
	<meta charset="UTF-8">
	<title><?php echo $page; ?></title>
	<style>
		nav a.active {
			background: black;
			color: white;
		}
	</style>
</head>
<body>
	<nav>
		<a href="/" class="<?php if ($page=='Home') { echo 'active'; } ?>">Home Page</a>
		<a href="/web_abc/resume.html" class="<?php if ($page=='Resume') { echo 'active'; } ?>">Resume</a>
		<a href="/web_abc/biography.html" class="<?php if ($page=='Bio') { echo 'active'; } ?>">Biogragphy</a>
	</nav>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

這裡利用了PHP動態產生`.active`這個Class以凸顯當前頁面的那個連結，那麼在其他頁面中要如何設定才可以正常運作呢。或者，大家有什麼其他的做法呢？動腦想想看吧！

{% hint style="danger" %}
伺服器使用完畢之後，請務必回到XAMPP Control Panel將Apache按下Stop關閉。
{% endhint %}

## A Break Time

下一節，我們就要來試著把網頁放到伺服器上。

