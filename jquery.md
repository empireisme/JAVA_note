# JQuery

## 複習筆記

```javascript
<h1 id="h" onclick="f1()">this is heading 1</h1>
<input type="text" id="idInp" value="123">

//JavaScript
let hObj=document.getElementById("h");  //object element取得物件
let hObj=document.querySelector("#h");  //object element
let hObjContent=hObj.innerHTML;  //textContent,innerText
let hObjContent=hObj.innerText;  //textContent取得內容
let hObjContent=hObj.textContent; 
console.log(document.querySelector("#idInp").value); 
//event handler
hObj.onclick=f1;
hObj.onclick=function(){...};
hObj.addEventListener("click",f1);
//this
hObj.style.color="red";

//jQuery
jQuery("selector");

let hSelector=jQuery("#h");  //selector array like object  取得選擇器
console.log(hSelector[0]);  //object element
let hSelectorContent=hSelector.html();  //method 
let hSelectorContent=hSelector.text();
console.log($("#idInp").val());
$("#h").click(function(){...});
$("#h").on("click",f1);
$("#h").on("click",function(){...});
//$(this)
$("#h").css("color","red");





```

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>01documentReady.html</title>
    <script src="https://code.jquery.com/jquery-3.6.0.js" integrity="sha256-H+K7U5CnXl1h5ywQfKtSj8PCmoN9aaq30gDh27Xc0jk=" crossorigin="anonymous"></script>
    <script>
        //JS
        // document.addEventListener("DOMContentLoaded",function(){
        //     $("h1").css("color","red");
        // })
        //jQuery
        //ready是一個事件，等到DOMTree產生後會執行這個事件
        // jQuery(document).ready(function(){
            
        //  })
        //jQuery 省略ready
         $(function(){
            $("h1").css("color","green");
         })
        
    </script>
    <script>
    
    </script>
</head>
<body>
    <h1>write less,do more</h1> 
    <h1>write more,do less</h1>
    <!-- <script src="../js/jquery-3.6.0.min.js"></script> -->

</body>
</html>
```

## this vs $\(this\)

```javascript
<!doctype html>
<html lang="zh-TW">

<head>
  <meta charset="utf-8">
  <title>04hover.html</title>
  <style>
    p {
      background: yellow;
    }
  </style>
</head>

<body>
  <p>
    Hello, <span>Person</span> <em>and person</em>.
  </p>

  <p id="idp">ppppppppppp</p>

  <script src="../js/jquery-3.6.0.min.js"></script>
  <script>
    $("p").hover(function () {
      // $(this).css("color","red");//用selector改
      this.style.color = "red";//用js去改顏色
    }, function () {
      $(this).css("color", "blue");
    });

    $("#idp").hover(function () {
      $(this).css("color", "green");
    }, function () {
      $(this).css("color", "purple");
    });
  </script>
</body>

</html>
```

## 動態binding

```javascript
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>05eventBinding</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>
<body> 
    <div class="container">
    <table id="idtable" class="table table-bordered table-sm" >
            <tr>
                <td>A0</td>
                <td>B1</td>
                <td>C2</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
            <tr>
                <td>D3</td>
                <td>E4</td>
                <td>F5</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
            <tr>
                <td>G6</td>
                <td>H7</td>
                <td>I8</td>
                <td><a href="#" class="btn btn-danger">刪除</a></td>
            </tr>
        </table>
        <input class="btn btn-primary" type="button" value="add row" id="buttonAdd" >
    </div>
    <script src="../js/jquery-3.6.0.min.js"></script>
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
            $("#idtable").on("click",".btn-danger",function(){
                $(this).closest("tr").remove(); 
            })

            

            $('#buttonAdd').click(function () {
                $('table').append("<tr><td>X</td><td>Y</td><td>Z</td><td><a href='#' class='btn btn-danger'>刪除</a></td></tr>");                    
            });                                       
        </script>
</body>
</html>
```

## APPEND

```javascript
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>05AppendRemove</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.8.1/css/all.css" integrity="sha384-50oBUHEmvpQ+1lW4y57PTFmhCaXp0ML5d60M1M7uH2+nqUivzIebhndOJK28anvf" crossorigin="anonymous">
</head>
  <body>
      <div class="container">
          <div class="py-2">
              <form class="form-inline">
                  <div class="form-group mr-2">
                      <label for="" class="mr-2">姓名</label>
                      <input type="text" name="" id="name" class="form-control" placeholder="" aria-describedby="helpId">
                  </div>
                  <div class="form-group mr-2">
                        <label for="" class="mr-2">電話</label>
                        <input type="tel" name="" id="tel" class="form-control" placeholder="" aria-describedby="helpId">
                    </div>
                    <div class="form-group mr-2">
                            <label for="" class="mr-2">email</label>
                            <input type="email" name="" id="email" class="form-control" placeholder="" aria-describedby="helpId">
                        </div>
                        <div class="form-group">
                            <a class="btn btn-primary text-white" id="add"><i class="fas fa-user-plus"></i></a>
                        </div>
              </form>
          </div>
        <table class="table table-bordered">
                <thead>
                    <tr>
                        <th>姓名</th>
                        <th>電話</th>
                        <th>email</th>
                        <th>操作</th>
                    </tr>
                </thead>
                <tbody id="tbody">
                    <!-- <tr>
                        <td>John</td>
                        <td>0900000000</td>
                        <td>john@test.com</td>
                        <td>
                            <button type="button" class="btn btn-primary"><i class="fas fa-trash-alt"></i></button>
                        </td>
                    </tr> -->
                </tbody>
        </table>
      </div>
      <script src="../js/jquery-3.6.0.min.js"></script>
      <script>
            $("#add").click(function(){
                let name=$("#name").val()
                let tel=$("#tel").val()
                let email=$("#email").val()
                let newrow=`<tr>
                        <td>${name}</td>
                        <td>${tel}</td>
                        <td>${email}</td>
                        <td>
                            <button type="button" class="btn btn-primary"><i class="fas fa-trash-alt"></i></button>
                        </td>
                    </tr>`;
                    $("#tbody").append(newrow);
            });
      </script>
</body>
</html>
```

![](.gitbook/assets/image%20%2827%29.png)

## 點甚麼便甚麼

```javascript
<!doctype html>
<html lang="en">
  <head>
    <title>04PhotoaddClass.html</title>
    <meta charset="utf-8">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <style>
        figure{
            width:20%;
            border: 4px solid transparent;
            margin: 4px;
            width: 120px;
            height: 120px;
        }
        figure.active{
            border: 4px solid red;
        }
        figure img{
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    </style>
  </head>
  <body>
      <div class="container">
          <div class="py-2 text-center">
              <img id="mainPic" src="images/pokemon1.png" alt="">
          </div> 
          <div class="d-flex justify-content-center">
              <figure class="active">
                  <img src="images/pokemon1.png" alt="">
              </figure>
              <figure>
                    <img src="images/pokemon2.png" alt="">
                </figure>
                <figure>
                        <img src="images/pokemon3.png" alt="">
                    </figure>
                    <figure>
                            <img src="images/pokemon4.png" alt="">
                        </figure>
                        <figure>
                                <img src="images/pokemon5.png" alt="">
                            </figure>
          </div>
      </div>
      <script src="../js/jquery-3.6.0.min.js"></script>
      <script>
        $("figure").click(function(){
            console.log(this);
            let pic=$(this).find("img").attr("src");
            console.log(pic)
            $("#mainPic").attr("src",pic)
            $(this).addClass("active")
            .siblings().removeClass("active")


            
        });
    </script>
  </body>
</html>
```

![](.gitbook/assets/image%20%2828%29.png)

