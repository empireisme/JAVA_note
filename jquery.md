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

