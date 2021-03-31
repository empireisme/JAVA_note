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

