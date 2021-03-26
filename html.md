# HTML

## 標籤筆記

\*每一個元素依據其開始及結束的位置分為二種: 1. block:佔一整列前後有其他元素會上下換行產生 ex:...，

## 清單範例

```markup
<!DOCTYPE html>
<html lang="zh-Hant-TW">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>清單元素</title>
</head>
<body>
    <h2>資策會訓練課程</h2>
    <ul style="background-color: yellow;">
        <li style="background-color: rgb(255, 38, 0);"> 就業養成班 </li>
        <li>軟體設計精修班</li>

    </ul>
    <h2>資策會訓練課程</h2>
    <ol type="I">
        <li>就業養成班</li>
        <li>軟體設計精修班</li>
    </ol>
</body>
</html>
```

![](.gitbook/assets/image%20%2822%29.png)

## 超連結

```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <a href="https://shopping.pchome.com.tw/">pc home</a>
    <a href="first.html">asdf</a> 
    <a href="mailto:a57249683012@gmail.com">mail to me</a>
</body>
</html>
```

![](.gitbook/assets/image%20%2823%29.png)

## CSS

```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .str1{
            color: yellow;
        }
        .str2{
            color: tomato;
        }
    </style>
</head>
<body>
    <h1 class="str1">我是標楷體</h1>
    <h1 class="str2">我是標楷體</h1>
    
</body>
</html>
```

![](.gitbook/assets/image%20%2824%29.png)

