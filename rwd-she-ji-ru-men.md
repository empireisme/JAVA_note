# RWD設計入門

## 利用Media方法以及flost來控制

```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        h1{
            color:blue;
        }
        @media (max-width: 500px),print{
            h1{
                color: red;
                font-size: 100px;
            }
        }
    </style>
</head>
<body>
    <h1>測試</h1>
</body>
</html>
```

當螢幕寬度小於500pixel的時候，便會將字體變成紅色外加字的大小變成100px

## 字體font設定外加使用link技巧

使用link技巧可以讓css檔案分開放，之後集中在link.css這個檔案集中

```css
@import url('https://fonts.googleapis.com/css2?family=Train+One&display=swap');
@import url(st1.css);
@import url(font.css);
```

```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="styles/link.css">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Train+One&display=swap" >
    <style>
        

    </style>
</head>
<body>
    <h1 class="font1">APPle</h1>
    <h1 class="font2">orange</h1>
        <p>asfas;ldfja;sldkf</p>
    <div style="width: 200px;border: 1px solid blue;padding-top: 50px; padding-bottom: 50px;">沒有高度指定的對其文字 </div>
    
</body>
</html>
```

## 好看的表單範例

```markup
<!DOCTYPE html>
<html lang="zh-Hant-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Input Type</title>
    <style>
        .t1 {
            width:100px;
            float:left;
            text-align:right;
        }
    </style>
</head>
<body>
    <form action="#" method="get">
        <p>  
            <label class="t1" for="">date:</label>
            <input type="date" name="date1">   
        </p>
        <p>   
            <label for="" class="t1">datetime:</label>
            <input type="datetime-local" name="dt1">     
        </p>
        <p>
            <label for="" class="t1">month:</label>
            <input type="month" name="month1">
        </p>
        <p>
            <label for="" class="t1">time:</label>
            <input type="time" name="time1">
        </p>
        <p>
            <label for="" class="t1">week:</label>
            <input type="week" name="week1">
        </p>
        <p>
            <label class="t1">URL:</label>
            <input type="url" name="url1">
        </p>
        <input type="">
        <input type="submit" value="送出">
    </form>
</body>
</html>
```

## 資策會的網頁設計

```markup
<!DOCTYPE html>
<html lang="zh-tw">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>RWD 網頁測試</title>
    <link rel="stylesheet" href="styles/rwd.css">
    <link rel="stylesheet" media="screen and  (max-width: 780px)" href="styles/rwd780.css" />
    <style>
        
    </style>
</head>
<body>
    <div id="allpage">
        <header>
            <img class="logo-img" src="image/logo.jpg" title="logo" alt="logo">
            <nav>
                <ul class="menu">
                    <li><a href="">首頁</a></li>
                    <li><a href="">關於</a></li>
                    <li><a href="">部落格</a></li>
                    <li><a href="">聯絡</a></li>
                </ul>
            </nav>            
        </header>
        <div id="content">
            <article class="article">
                <section class="section">
                    <h2><a href="https://zh.wikipedia.org/wiki/HTML5">HTML5</a></h2>                    
                    <p>HTML5是HTML最新的修訂版本，由全球資訊網協會（W3C）於2014年10月完成標準制定[2][4]。目標是取代1999年所制定的HTML 4.01和XHTML 1.0標準，以期能在網際網路應用迅速發展的時候，使網路標準達到符合當代的網路需求。廣義論及HTML5時，實際指的是包括HTML、CSS和JavaScript在內的一套技術組合。它希望能夠減少網頁瀏覽器對於需要外掛程式的豐富性網路應用服務（Plug-in-Based Rich Internet Application，RIA），例如：Adobe Flash、Microsoft Silverlight與Oracle JavaFX的需求，並且提供更多能有效加強網路應用的標準集。</p>
                    <p>HTML5添加了許多新的語法特徵，其中包括video、audio和canvas元素，同時整合了SVG內容。這些元素是為了更容易的在網頁中添加和處理多媒體和圖片內容而添加的。其它新的元素如section、article、header和nav則是為了豐富文件的資料內容。新的屬性的添加也是為了同樣的目的。同時也有一些屬性和元素被移除掉了。一些元素，像a、cite和menu被修改，重新定義或標準化了。同時APIs和DOM已經成為HTML5中的基礎部分了。HTML5還定義了處理非法文件的具體細節，使得所有瀏覽器和用戶端程式能夠一致地處理語法錯誤。</p>
                </section>                
            </article>
            <aside class="aside">
                    <section class="section">
                            <h2><a href="https://zh.wikipedia.org/wiki/%E5%B1%82%E5%8F%A0%E6%A0%B7%E5%BC%8F%E8%A1%A8">CSS3</a></h2>                           
                            <p>層疊樣式表（英語：Cascading Style Sheets，縮寫：CSS；又稱串樣式列表、級聯樣式表、串接樣式表、階層式樣式表）是一種用來為結構化文件（如HTML文件或XML應用）添加樣式（字型、間距和顏色等）的電腦語言，由W3C定義和維護。目前最新版本是CSS2.1，為W3C的推薦標準。CSS3現在已被大部分現代瀏覽器支援，而下一版的CSS4仍在開發中。</p>
                    </section>
            </aside>
        </div>  <!--end content-->
        <footer>
                <p>2014 All Rights Reserved Quality Art Technology CO. </p>
        </footer>
    </div>  <!--end allpage-->
</body>
</html>
```

```css
body {
    background-color:	#ECF5FF;
    
}
* {
    margin:0;
    padding:0;
}
#allpage {
    width:70%;
    margin:0 auto;
}
header {
    width:100%;
}
.logo-img {
    width:100%;
    
}
.menu {
    width:100%;
    overflow:auto;            
    background-color:#ACD6FF;
    border-radius:5px;
    list-style-type:none;
   
}
.menu li {
    width:7em;
    line-height:2.5em;
    float:left;
    
}
.menu li a {
    display:block;
    text-align:center;
    color:	#005AB5;
}
.menu li a:link {
    text-decoration:none;
}
.menu li a:hover {
    background-color:	#0080FF	;
    color:	#ffffff;
    border-radius:5px;
}
#content {
    width:100%;
    overflow:auto;
}
.article {
    width:70%;
    float:left;
}
.section {
    background-color:#ffffff;
    border-radius:5px;
    margin:10px 0;
    padding:20px 26px;
    line-height:2em;
}

.aside {
    width:28%;
    float:right;
    
}
footer {
    background-color:	#ACD6FF;
    border-radius:5px;
    text-align:center;
    line-height:2.5em;
    color:	#4F4F4F;
}
```

