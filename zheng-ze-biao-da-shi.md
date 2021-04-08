# 正則表達式

```markup
<!DOCTYPE html>
<html lang="zh-tw">
<head>
    <meta charset="UTF-8">
    <title>10regExpObject.html</title>
</head>
<body>
    <label>Email:</label><input type="text" id="idEmail" />
    <br />
    <input type="button" value="checkEmail" onclick="chkEmail();" />
    <script>

            let str="Is this all there is?";
            let re=new RegExp("is","gi");//這個字串有is嗎
            console.log(str.match(re));
            re=new RegExp("is","i");//這個字串有is嗎
            console.log(str.match(re));	
            re=new RegExp("is","g");//這個字串有is嗎
            console.log(str.match(re));	

            function chkEmail() {
                //取得元素值
                let theEmail = document.getElementById("idEmail").value;
                //建立RegExp物件語法 2
                let re1 = /^.+@.+\..{2,3}$/; //literal RegExp
                //建立RegExp物件語法 1
                let re=new RegExp("^.+@.+\\..{2,3}$")
                //因為寫在字串裡面，事故需要兩個斜線，一再強調literal的好處
                alert(`re1=${re1}\nre=${re}`)
                if (re.test(theEmail))
                    window.alert("successful");
                else
                    window.alert("failure");
    
            }
        </script>
</body>
</html>

```

{% embed url="https://docs.google.com/document/d/1mSxRmAUx-rm0wJ9MtkISwTemZmilFguXhMLavy-zxkg/edit\#" %}

{% embed url="https://ithelp.ithome.com.tw/articles/10094951" %}

## HW2

```markup
<!DOCTYPE html>
<html lang="zh-tw">
<head>
    <meta charset="UTF-8">
    <title>Hw2表單驗證.html</title>
    <style>
        fieldset{
            width: 500px;
            border: 3px solid red;
            margin:15px;
        }
    </style>
</head>
<body>
    
    <fieldset>
        <legend>Form check</legend>
   
    <div>
        <label for="">姓名:</label>
        <input type="text" id="idName" size=6>
        <span id="idspName"> </span>
        <br>1.不可空白2.至少兩個字以上3.必須全為中文字
    </div>

    <div>
        <label>密碼:</label>
        <input type="password" id="idPwd" size="6" /><!-- 瀏覽器執行到此標籤會建立一個物件-->
        <span id="idsp"></span><br/>  
        1.不可空白2.至少6個字，且包含英數字、特殊字元
    </div>

    <div>
        <label for="">日期:</label>
        <input type="text" id="idDate" size=6>
        <br>格式:西元年/月/日(yyyy/mm/dd)
    </div>
</fieldset>
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
                sp.innerHTML="<img src='error.png'>you must enter"; 
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
        document.getElementById("idName").onblur=checkName;
        function checkName(){
            let theNameObj=document.getElementById("idName");
            let theNameObjVal=theNameObj.value;
            console.log(theNameObjVal);
            let sp=document.getElementById("idspName");
            regex=/[\u4E00-\u9FA5]{2,}/;
            flag=regex.test(theNameObjVal,"gi");
            console.log(flag);
            if(flag){
                sp.innerHTML="correct";
            }else{
                sp.innerHTML="<img src='error.png'>請輸入符合格式的文字";
            }
        }
    </script>
</body>
</html>

```



