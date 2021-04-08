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



