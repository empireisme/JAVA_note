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

## 利用link技巧讓所有css可以分開放，之後集中的引入

```css
@import url('https://fonts.googleapis.com/css2?family=Train+One&display=swap');
@import url(st1.css);
@import url(font.css);
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

