# 動態樣式

```markup
<!DOCTYPE html>
<html lang="zh-tw">
<head>
    <meta charset="UTF-8">
    <title>01dynamicStyle.html</title>
    <style>
        .n{
			color:blue;
			font-family:Arial;
			font-size:24px;
		}
		.s{
			color:red;
			font-family:"Script MT Bold";
			font-size:36px;
		}
    </style>
    <script>
        document.addEventListener("DOMContentLoaded", function () {
            document.getElementById("h").addEventListener("mouseover",mouseOver);  //事件繫結，滑鼠滑入
            document.getElementById("h").addEventListener("mouseout",mouseOut);    //事件繫結，滑鼠滑出
        });

        function mouseOver() {
            //動態樣式改變，方法 1
            // document.getElementById("h").style.color="red";
            //動態樣式改變，方法 2
            // document.getElementById("h").className="s"
            this.className="s"
        }

        function mouseOut() {
            //動態樣式改變，方法 1
            // document.getElementById("h").style.color="blue";
            //動態樣式改變，方法 2
            // document.getElementById("h").className="n"
            this.className="n"
        }
    </script>
</head>
<body>
    <h1 id="h" class="n" >this is heading 1</h1>
</body>
</html>
```

## insertAdjacentHTML

```markup
<!DOCTYPE html>
<html lang="zh-tw">
<head>
    <meta charset="UTF-8">
    <title>04checkPassword.html</title>
</head>
<body>
    <label>Password:</label>
    <input type="password" id="idPwd" size="6" /><!-- 瀏覽器執行到此標籤會建立一個物件-->
    <span id="idsp"></span><br/>    
    <!-- <input type="button" id="idbut" value="checkPassword" onclick="checkPwd();" /> -->

    <script>
        document.getElementById("idPwd").onblur=checkPwd;
        function checkPwd(){
            //取得idPwd元素
            let thePwdObj=document.getElementById("idPwd");
            console.log(thePwdObj);
            //取得idPwd元素值
            let thePwdObjVal=thePwdObj.value;
            console.log(thePwdObjVal);
            console.log(typeof thePwdObjVal);

            //判斷元素值是否為空白，密碼長度是否大於6
            //如果長度是否大於6，判斷是否包含字母、數字、特殊符號
            let sp=document.getElementById("idsp");
            let thePwdObjValLen=thePwdObjVal.length;
            let flag1=false,flag2=false,flag3=false;

            if(thePwdObjVal=="")
                // sp.innerHTML="<img src='Images/error.png'>you must enter"; 
                document.getElementById("idPwd").insertAdjacentHTML("afterend", "add AfterEnd zzzzz");
                //看出insert 方法有問題
                else if(thePwdObjValLen>=6){
                // sp.innerHTML=">=6";
                for(let i=0;i<thePwdObjValLen;i++){
                    let ch=thePwdObjVal.charAt(i).toUpperCase();
                    if(ch>="A" && ch<="Z")
                        flag1=true;
                    else if(ch>="0" && ch<="9")
                        flag2=true;
                    if(flag1 && flag2) break;
                }
                if(flag1 && flag2)
                    sp.innerHTML="correct";
                else
                    sp.innerHTML="incorrect";
            }else{
                sp.innerHTML="Password length must be greater than 6";
            }     
        }        
    </script>
</body>
</html>

```

## 氣泡設定

```markup
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title>06eventTargetcurrentTarget.html</title>
    <script>
        //==============================================================
        //階層式標籤，事件流程分三階段，
        //事件捕獲(capture)階段==>處理目標階段==>事件氣泡(bubbling)階段
        //==============================================================
        document.addEventListener("DOMContentLoaded", function () {
            document.getElementById("idp").addEventListener("click",clickP); //事件繫結，事件氣泡(bubbling)
            document.getElementById("idbut").addEventListener("click",clickBut);
        });
        

        //target：回傳觸發事件的元素 被你click的元素
        //currentTarget：回傳事件正在處理時所在的元素
        //[object class] 一個物件的類別(class)屬性是個字串，提供關於該物件的種類的資訊
        function clickP(nsevent) {
            alert("input target="+event.target.id+
            "\n p currentTarget="+event.currentTarget.id+
            "\n p this="+this.id
            );   
            // console.log("p");
            // console.log(nsevent.target)
        }

        function clickBut() {
            alert("input target="+event.target.id+
            "\n p currentTarget="+event.currentTarget.id
            );
            

        }
    </script>
</head>
<body>
    <p id="idp">
       <input type="button" id="idbut" value="button" />            
    </p>
</body>
</html>

```

## MAP

```markup
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title>11imageObject.html</title>
    <link rel="icon" href="images/EEIT_logo.png" type="image/x-icon" />
    <script>
        //=============================================================
        //1. 使用<area>物件的id
        //2. 使用 document.getElementsByTagName("area")取得所有area元素
        //3. 使用 document.querySelectorAll("area")取得所有area元素(slide 93)  
        //=============================================================
        document.addEventListener("DOMContentLoaded", function () {
            document.querySelector("#idTaipei").addEventListener("mouseover",mouseOver);//事件繫結
            document.querySelector("#idTaipei").addEventListener("mouseout",mouseOut);
            document.querySelector("#idTaipei").addEventListener("click",Click);           
        });  

        function mouseOver() {            
            document.images[0].src = "images/MapTaipei.gif";          
        }


        function mouseOut() {            
            document.images[0].src = "images/map00.gif";
        }


        function Click() {            
            document.getElementById("mapdiv").innerHTML = "<img src='images/Taipei.gif'/>";
        }
    </script>
</head>
<body>
    <div style="float:left;width:200px;height:343px;margin-top:20px;">
        <img id="imgMap" alt="" src="images/map00.gif"  usemap="#FPMap0"/>
            <map id="FPMap0" name="FPMap0">
                <area  id="idTaipei" coords="136,21,144,13,151,29,145,38,136,21"  shape="poly" />
                <area  id="idTaoyuan" coords="95,38,120,22,132,34,125,45,138,64,128,78,95,37"  shape="poly" />
                <area  id="idTaichung" coords="46,113,58,89,87,104,120,91,134,100,122,113,81,122,70,134,45,112,45,112"  shape="poly" />
                <area  id="idKaohsiung" coords="18,241,39,242,86,185,98,201,76,243,72,250,46,251,39,283,25,259,18,240"  shape="poly" />
            </map>
    </div>
    <div id="mapdiv" style="float:left;width:auto;height:auto;"></div>
</body>
</html>

```

## MOUSE OVER

```markup
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title>11imageObject.html</title>
    <link rel="icon" href="images/EEIT_logo.png" type="image/x-icon" />
    <script>
        //=============================================================
        //1. 使用<area>物件的id
        //2. 使用 document.getElementsByTagName("area")取得所有area元素
        //3. 使用 document.querySelectorAll("area")取得所有area元素(slide 93)  
        //=============================================================
        document.addEventListener("DOMContentLoaded", function () {
           // 1. document.querySelector("#idTaipei").addEventListener("mouseover",mouseOver);//事件繫結
            // document.querySelector("#idTaipei").addEventListener("mouseout",mouseOut);
            // document.querySelector("#idTaipei").addEventListener("click",Click); 
            // document.querySelector("#idTaoyuan").addEventListener("mouseover",mouseOver);//事件繫結
            // document.querySelector("#idTaoyuan").addEventListener("mouseout",mouseOut);
            // document.querySelector("#idTaoyuan").addEventListener("click",Click);      
            
            //2. let areas=document.getElementsByTagName("area");
            let areas=document.querySelectorAll("area.imgbtn");
            //可以更細緻的去定義
            let areasLen=areas.length;
            console.log(areas);
            console.log(areas.length);
            for(let i=0;i<areasLen;i++){
                areas[i].addEventListener("mouseover",mouseOver);
                areas[i].addEventListener("mouseout",mouseOut);
                areas[i].addEventListener("click",Click)
            }
        });  

        function mouseOver() {   
            console.log(this);
            console.log(this.id);    
            document.getElementById("imgMap").src="images/Map"+this.id.substr(2)+".gif";
        }//滑入要畫圖


        function mouseOut() {            
            document.images[0].src = "images/map00.gif";
        }//滑出要復原


        function Click() {            
            document.getElementById("mapdiv").innerHTML =
             "<img src='images/"+this.id.substr(2)+".gif'/>";
        }
    </script>
</head>
<body>
    <div style="float:left;width:200px;height:343px;margin-top:20px;">
        <img id="imgMap" alt="" src="images/map00.gif"  usemap="#FPMap0"/>
            <map id="FPMap0" name="FPMap0">
                <area  id="idTaipei" class="imgbtn" coords="136,21,144,13,151,29,145,38,136,21"  shape="poly" />
                <area  id="idTaoyuan" class="imgbtn" coords="95,38,120,22,132,34,125,45,138,64,128,78,95,37"  shape="poly" />
                <area  id="idTaichung"  coords="46,113,58,89,87,104,120,91,134,100,122,113,81,122,70,134,45,112,45,112"  shape="poly" />
                <area  id="idKaohsiung" class="imgbtn" coords="18,241,39,242,86,185,98,201,76,243,72,250,46,251,39,283,25,259,18,240"  shape="poly" />
            </map>
    </div>
    <div id="mapdiv" style="float:left;width:auto;height:auto;"></div>
</body>
</html>


```

## 表單的驗證

```markup
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title>12formObject.html</title>
    <script>
        document.addEventListener("DOMContentLoaded", function () {
            document.querySelector("#idbutton").addEventListener("click",checkf);//事件繫結
            document.querySelector("#idreset").addEventListener("click",resetf);
            document.querySelector("#idsubmit").addEventListener("click",submitf);
        });

        function checkf() {

        }

        function resetf() {
            document.forms[0].reset();
        }

        function submitf() {
            if(document.getElementById("idname").value=="")
               alert("please type something")
            else{
                document.forms[0].submit()
            }
        }
    </script>
</head>
<body>
    <form action="get.jsp" method="get">
			<label>name:</label><input type="text" id="idname" name="txtName" value="abc" /><span id="idsp"></span><br/>
			<input type="checkbox" name="hobby" checked="checked" value="reading"/>reading
			<input type="checkbox" name="hobby" value="game"/>game
			<input type="checkbox" name="hobby" value="sleep"/>sleep
			<br/>
            <input type="submit" value="送出" />	
            <input id="idbutton" type="button" value="check" />
            <input id="idreset" type="button" value="reset" />
			<input id="idsubmit" type="button" value="submit" />
	</form>
</body>
</html>
```

{% file src=".gitbook/assets/jshomework.zip" %}

## dom介紹

```markup
<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>01DOM.html</title>
    <script>
        //*****************************************
        //nodeName 讀取元素節點內容，得到是元素名稱
        //nodeValue 讀取文字節點內容，得到的是文字內容
        //nodeType 讀取節點類型
        //*****************************************

        document.addEventListener("DOMContentLoaded", function () {
            // alert(document.nodeType);  //9
            // alert(document.nodeName);  //#document
            // alert(document.nodeValue);  //null

            //取得根元素 documentElement
            let root = document.documentElement;  //HTML
            // alert(root.nodeType);  //1
            // alert(root.nodeName);  //HTML
            // alert(root.nodeValue);  //null

            let thebody = root.childNodes[1];  //BODY
            // alert(thebody.nodeName);//body
            // alert(thebody.childNodes[1].nodeName);//p
            // alert(thebody.childNodes[1].firstChild.nodeValue); //i am a javascript
            // alert(thebody.childNodes[1].childNodes[0].nodeValue);

            let theNode = root.childNodes[1].childNodes[3].childNodes[3];  //LI
            // alert(root.childNodes[1].childNodes[3].nodeName);
            // alert(theNode.nodeName);
            //alert(theNode.firstChild.nodeValue);  //bbbbb
            //alert(theNode.previousSibling.previousSibling.firstChild.nodeValue);  //aaaaa
            //alert(theNode.nextSibling.nextSibling.firstChild.nodeValue);  //ccccc

            //alert(theNode.parentNode.nodeName);  //UL
            //alert(theNode.parentNode.lastChild.previousSibling.firstChild.nodeValue);  //fffff


            let lis = document.getElementsByTagName("li");
            for (let i = 0; i < lis.length; i++) {
                console.log(lis.item(0));
                //ITEM是方法，所以用小括弧
                alert(lis.item(i).firstChild.nodeValue);
                //alert(lis[i].firstChild.nodeValue);
                //ARRAY LIKE 顧可以用索引
            }


        });
    </script>
</head><body><h1>Hello DOM</h1><p>I am a JavaScript</p>
    <ul>     
        <!-- childnode3 -->
        <li>aaaaa</li>
        <li>bbbbb</li>
        <li>ccccc</li>
        <li>ddddd</li>
        <li>eeeee</li>
        <li>fffff</li>
    </ul>
</body>

</html>
```

## DOM進階

```markup
<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>02DOM2.html</title>
    <script>
        document.addEventListener("DOMContentLoaded", function () {
            document.querySelector("#CEle").addEventListener("click", CreateElement)
            document.querySelector("#REle").addEventListener("click",RemoveElement)
        });
        function RemoveElement(){
            let theNode=document.getElementById("idImg");
            theNode.parentNode.removeChild(theNode);//old method
            theNode.remove();//new method
        }

        function CreateElement() {
            let theDIV = document.querySelector("#iddiv");  //取得div物件

            let eleP = document.createElement("p");//<P><P/>
            let txtP = document.createTextNode("Hello World");//HELLO WORLD
            eleP.appendChild(txtP);//<p>

            theDIV.appendChild(eleP);

            let eleImg = document.createElement("img");
            eleImg.setAttribute("src", "DOM/DOMImage/rabbit-hat.gif");
            eleImg.setAttribute("id","idImg")
            theDIV.appendChild(eleImg);
            //
        }
    </script>
</head>

<body>
    <div id="iddiv">div</div>
    <input type="button" id="CEle" value="CreateElement">
    <input type="button" id="REle" value="RemoveElement">

</body>
</html>

```

