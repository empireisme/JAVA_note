# CSS

## 表格

```css
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .tb1 {
            width: 400px;
            border: 3px solid blue;
            border-collapse: collapse;
        }

        td,
        th {
            border: 1px solid gray;
        }

        thead {
            background-color: hotpink;
            color: #ffffff;
            text-transform: capitalize;
        }

        tbody {
            background-color: darkcyan;
            text-align: center;
        }
        tbody tr:nth-child(2n){
            background-color: darkorchid;
        }
        tbody tr:nth-child(2n+1){
            background-color:darkolivegreen;
        }
        tbody tr:hover{
            background-color: firebrick;
        }
        tbody td:hover{
            background-color: lightblue;
        }
    </style>
</head>

<body>
    <table class="tb1">
        <thead>
            <tr>
                <th>column1</th>
                <th>column2</th>
                <th>column3</th>
                <th>column4</th>
            </tr>
            <tr>
                <th colspan="2">column1</th>
                <th colspan="2">column2</th>

            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td>2</td>
                <td>3</td>
                <td>4</td>
            </tr>
            <tr>
                <td>1</td>
                <td>2</td>
                <td rowspan="3">3</td>
                <td>4</td>
            </tr>
            <tr>
                <td>1</td>
                <td>2</td>

                <td>4</td>
            </tr>
            <tr>
                <td>1</td>
                <td>2</td>

                <td>4</td>
            </tr>
        </tbody>
    </table>
</body>

</html>
```

## 表單

```css
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .st1{
            width: 450px;
            border-bottom: 3px dotted blue;
            margin: 20px;
            padding-bottom: 10px;
        }
        .sub{
            width: 450px;
            margin: 20px;
            text-align: center;
        }
        .t1{
            width: 100px;
            float: left;
            text-align: right;
        }
        textarea{
            resize:none;
        }
    </style>
</head>

<body>
    <form action="#" method="POST" enctype="multipart/form-data">
        <div class="st1">
            <label class="t1" for="account1">姓名:</label>
            <input type="text" id="account1" name="account" value="guest" size="10">
        </div>
        <div class="st1">
            <label class="t1">性別</label>
            <input type="radio" name="gender" value="male" id="m1">
            <label for="m1">男生</label>
            <input type="radio" name="gender" value="female" id="m2">
            <label for="m2">女生</label>
        </div>
        <div class="st1">
            <label for="" class="t1">興趣</label>
            <label >
                <input type="checkbox" name="hobby" value="music">音樂
            </label>
            <label >
                <input type="checkbox" name="hobby" value="sport">運動
            </label>
        </div>

        <div class="st1">
            <label class="t1" for="password1">密碼:</label>
            <input id="password1" type="password" name="pwd">
        </div>

        <div class="st1">
            <label class="t1" for="comment1">意見:</label>
            <textarea id="comment1" name="comment"  cols="40" rows="3"></textarea>
        </div>
        <div class="st1">
            <label for="" class="t1">縣市</label>
            <select name="add1" multiple>
                <option value="tpe">台北市</option>
                <option value="tph"   selected>新北市</option>
            </select>

        </div>
        <div class="st1">
            <label for="" class="t1">照片</label>
            <input type="file" name="file1">
        </div>
        <div class="sub">
            <input type="submit" value="送出">
            <input type="reset" value="清除">
        </div>

    </form>
</body>

</html>
```

## 作業解答

{% file src=".gitbook/assets/htmlsolution.html" %}

## 老師範例

{% file src=".gitbook/assets/range-number.html" %}

{% file src=".gitbook/assets/form\_example.html" %}

## datalist and list

```markup
<html>
<body>

<input list="cars" />
<datalist id="cars">
	<option value="BMW">
	<option value="Ford">
	<option value="Volvo">
</datalist>

</body>
</html>
```

![](.gitbook/assets/image%20%2825%29.png)

