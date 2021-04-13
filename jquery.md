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

