# 期中專題小組

## 有用的stackoverflow

{% embed url="https://stackoverflow.com/questions/5003142/show-jdbc-resultset-in-html-in-jsp-page-using-mvc-and-dao-pattern" %}



菜單提交的bug

```markup
<!DOCTYPE html>
<html lang="zh-TW">

<head>
    <meta charset="UTF-8">
    <title>05eventBinding</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>

<body>
    <h1>新增菜單</h1>
    <div class="container">
        <form>
        <table id="idtable" class="table table-bordered table-sm" contenteditable='true'>
            <thead>
                <tr>
                    <th scope="col">品名</th>
                    <th scope="col">價錢</th>
                    <th scope="col">介紹</th>
                    <th scope="col">功能</th>
                </tr>
            </thead>
            <tr>
                <td>請輸入品名</td>
                <td>請輸入價錢</td>
                <td>請輸入介紹</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
            <tr>
                <td>請輸入品名</td>
                <td>請輸入價錢</td>
                <td>請輸入介紹</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
            <tr>
                <td>請輸入品名</td>
                <td>請輸入價錢</td>
                <td>請輸入介紹</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
        </table>
        <input class="btn btn-primary" type="button" value="add row" id="buttonAdd">
        <input class="btn btn-primary" type="submit"  value="提交" />
    </form>
        
    </div>

  


    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.0/jquery.min.js"></script>
    <script>
        //測試看看
        //按下刪除按鈕(class名稱是btn-danger)時,可以將那一筆資料刪除
        //再試試看
        //按下[add row]按鈕多新增幾筆資料
        //針對新增出來的資料,按下刪除按鈕(class名稱是btn-danger)時,還可以將那一筆資料刪除嗎???
        // $('.btn-danger').click(function () {
        //     //$(this).parent().parent().remove();
        //     // $(this).parents('tr').remove(); 
        //     $(this).closest("tr").remove();        
        // });   


        //練習使用on繫結網頁上刪除按鈕，完成刪除動作
        //此時新增的還不能山
        //此時要用動態binding才能動
        $("#idtable").on("click", ".btn-danger", function () {
            $(this).closest("tr").remove();
        })



        $('#buttonAdd').click(function () {
            $('table').append("<tr><td>請輸入品名</td><td>請輸入價錢</td><td>請輸入介紹</td><td><a href='#' class='btn btn-danger'>刪除</a></td></tr>");
        });
    </script>
</body>

</html>
```

### 自己解決尚未驗證的bug

```markup
<!DOCTYPE html>
<html lang="zh-TW">

<head>
    <meta charset="UTF-8">
    <title>05eventBinding</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>

<body>
    <h1>新增菜單</h1>
    <div class="container">
        <form>
        <table id="idtable" class="table table-bordered table-sm" contenteditable='true'>
            <thead>
                <tr>
                    <th scope="col">品名</th>
                    <th scope="col">價錢</th>
                    <th scope="col">介紹</th>
                    <th scope="col">功能</th>
                </tr>
            </thead>
            <tr>
                <td>請輸入品名</td>
                <td>請輸入價錢</td>
                <td>請輸入介紹</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
            <tr>
                <td>請輸入品名</td>
                <td>請輸入價錢</td>
                <td>請輸入介紹</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
            <tr>
                <td>請輸入品名</td>
                <td>請輸入價錢</td>
                <td>請輸入介紹</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
        </table>
        <input class="btn btn-primary" type="button"  value="add row" id="buttonAdd">
        <input class="btn btn-primary" type="submit"  value="提交" />
        <input class="btn btn-primary" type="button"  onclick="myFunction()" value="Submit form">
    </form>
        
    </div>


    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.0/jquery.min.js"></script>
    <script>
        $("#idtable").on("click", ".btn-danger", function () {
            $(this).closest("tr").remove();
        })



        $('#buttonAdd').click(function () {
            $('table').append("<tr><td>請輸入品名</td><td>請輸入價錢</td><td>請輸入介紹</td><td><a href='#' class='btn btn-danger'>刪除</a></td></tr>");
        });
        document.getElementById("myForm").submit();
    </script>
</body>

</html>
```



