# JS作業

## 換圖片技巧重點是id

![](.gitbook/assets/image%20%2858%29.png)

{% embed url="https://stackoverflow.com/questions/47067140/changing-image-src-on-button-click" %}

{% embed url="https://stackoverflow.com/questions/47067140/changing-image-src-on-button-click" %}

## 重購前

![](.gitbook/assets/image%20%2859%29.png)

```markup
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<script>
    //event binding
    document.addEventListener("DOMContentLoaded", function () {
        document.getElementById("idchangeNextImg").addEventListener("click", changeNextImg);
        // document.getElementById("idbutstop").addEventListener("click", stopf);
        document.getElementById("idchangeBeforeImg").addEventListener("click", changeBeforeImg);

        let counter = 1;
        function changeNextImg() {
            counter++;
            if (counter > 5) {
                counter = 1;
            }
            buildimg = `images/iphone${counter}.jpg`;
            document.getElementById("theImage").setAttribute('src', buildimg);

        }
        function changeBeforeImg() {
            counter--;
            if (counter < 1) {
                counter = 5;
            }
            buildimg = `images/iphone${counter}.jpg`;
            document.getElementById("theImage").setAttribute('src', buildimg);
        }
        // function show(){
        //     if (counter >5) {
        //         counter = 1;
        //     } 
        //     if (counter < 1) {
        //         counter = 5;
        //     }
        //     buildimg = `images/iphone${counter}.jpg`;
        //     document.getElementById("theImage").setAttribute('src', buildimg);
        // }
    });
</script>


<body>
    <div>
        <img id="theImage" src="images/iphone1.jpg" alt="" height="300">
        <p><input type="button" id="idchangeNextImg" value="換下一張圖片"></p>
        <p><input type="button" id="idchangeBeforeImg" value="換上一張圖片"></p>

    </div>


</body>

</html>
```

## 重購後

![](.gitbook/assets/image%20%2857%29.png)

```markup
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<script>
    //event binding
    document.addEventListener("DOMContentLoaded", function () {
        document.getElementById("idchangeNextImg").addEventListener("click", changeNextImg);
        // document.getElementById("idbutstop").addEventListener("click", stopf);
        document.getElementById("idchangeBeforeImg").addEventListener("click", changeBeforeImg);

        let counter = 1;
        function changeNextImg() {
        counter++;
        show();
        }
        function changeBeforeImg() {
            counter--;
            show();
        }
        function show(){
            if (counter >5) {
                counter = 1;
            } 
            if (counter < 1) {
                counter = 5;
            }
            buildimg = `images/iphone${counter}.jpg`;
            document.getElementById("theImage").setAttribute('src', buildimg);
        }
    });
</script>


<body>
    <div>
        <img id="theImage" src="images/iphone1.jpg" alt=""  height="300">
        <p><input type="button" id="idchangeNextImg" value="換下一張圖片"></p>
        <p><input type="button" id="idchangeBeforeImg" value="換上一張圖片"></p>

    </div>


</body>

</html>
```

## 檔案下載區

{% file src=".gitbook/assets/hw4.html" caption="hw4重購前" %}

{% file src=".gitbook/assets/hw4\_rebuild.html" caption="hw4重購後" %}

{% file src=".gitbook/assets/hw4.zip" caption="hw4\_all\_zip" %}

