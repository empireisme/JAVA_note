# 資策會Java筆記

## 關於我

**912394113**



## 參考的資料

{% embed url="https://morosedog.gitlab.io/categories/Spring-Boot/" %}

{% embed url="https://ithelp.ithome.com.tw/articles/10256275" %}

{% embed url="https://matthung0807.blogspot.com/2017/12/java-serviceinterface.html" %}



{% embed url="https://yubin551.gitbook.io/java-note/basic-object-oriented" %}

{% embed url="https://github.com/bridennis/java-crud-spa/tree/master/src/main/java/ru/javarush/internship/test" %}

{% embed url="https://ithelp.ithome.com.tw/users/20120911/ironman/2709?page=2" %}

{% embed url="https://matthung0807.blogspot.com/2020/09/servlet-simple-restful-api.html" %}

{% embed url="https://www.tutorialspoint.com/servlets/servlets-form-data.htm" %}

{% embed url="https://stackoverflow.com/questions/4112686/how-to-use-servlets-and-ajax" %}

{% embed url="https://www.geeksforgeeks.org/how-to-fetch-data-from-json-file-and-display-in-html-table-using-jquery/" %}

{% embed url="https://www.youtube.com/watch?v=konz-5tM\_7Q" %}



{% embed url="https://jsonplaceholder.typicode.com/posts" %}

{% embed url="https://howtocreateapps.com/fetch-and-display-json-html-javascript/" %}

## 面試問題

{% embed url="https://www.dineshonjava.com/interview-questions-on-spring/" %}

EXPRESS Middleware

{% embed url="https://hackmd.io/@Heidi-Liu/note-be201-express-middleware?fbclid=IwAR05NWpvecaABC6ofpKQ8108ilA13S0oypNPZ6tkHOBqjHyJjn9302yV494" %}

{% embed url="https://seanyeh.medium.com/express%E7%9A%84%E4%B8%AD%E4%BB%8B%E8%BB%9F%E9%AB%94-middleware-830cf052017d" %}

## 共同編輯

{% embed url="https://medium.com/front-end-weekly/build-a-collaborative-rich-text-editor-with-node-js-and-socket-io-38ee25b6e315" %}

## Getjsondata

{% embed url="https://zetcode.com/javascript/jsonurl/" %}

{% embed url="https://stackoverflow.com/questions/66448572/how-to-display-all-json-fetch-api-content-on-a-html-table-using-javascript" %}

{% embed url="https://stackoverflow.com/questions/66448572/how-to-display-all-json-fetch-api-content-on-a-html-table-using-javascript" %}

```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
   
        <table id="mytable">
            <thead>
                <tr>
                    <th colspan="2">The table header</th>
                    <th colspan="2">The table header</th>
                    <th colspan="2">The table header</th>
                    <th colspan="2">The table header</th>
                </tr> 
            </thead>
            <tbody>

            </tbody>
        </table>

</body>
</html>

<script>
fetch('https://jsonplaceholder.typicode.com/posts')
  .then((response) => response.json())
  .then((json) => json.forEach(tableElements)
  )

  function tableElements (element, index, arr){
    arr[index] = document.querySelector('#mytable').innerHTML +=
    `<tr>
        <td>${element.userId}</td>
        <td>${element.id}</td>
        <td>${element.title}</td>
        <td>${element.body}</td>
    </tr>`
  }
</script>


<!-- <script>
fetch("http://dummy.restapiexample.com/api/v1/employees").then(
  res => {
    res.json().then(
      data => {
        console.log(data.data);
        if (data.data.length > 0) {

          var temp = "";
          data.data.forEach((itemData) => {
            temp += "<tr>";
            temp += "<td>" + itemData.id + "</td>";
            temp += "<td>" + itemData.employee_name + "</td>";
            temp += "<td>" + itemData.employee_salary + "</td></tr>";
          });
          document.getElementById('data').innerHTML = temp;
        }
      }
    )
  }
)


</script> -->


<!-- <script>
    fetch('http://time.jsontest.com')
        .then(res => res.json())
        .then((out) => {
            console.log('Output: ', out);
    }).catch(err => console.error(err));
</script> -->
```

```markup
 MultipartFile productImage = bb.getProductImage();        String originalFilename = productImage.getOriginalFilename();        bb.setFileName(originalFilename);                String ext = originalFilename.substring(originalFilename.lastIndexOf("."));        String rootDirectory = context.getRealPath("/");        //  建立Blob物件，交由 Hibernate 寫入資料庫        if (productImage != null && !productImage.isEmpty() ) {            try {                byte[] b = productImage.getBytes();                Blob blo       }
```

```markup
 MultipartFile productImage = bb.getProductImage();        String originalFilename = productImage.getOriginalFilename();        bb.setFileName(originalFilename);                String ext = originalFilename.substring(originalFilename.lastIndexOf("."));        String rootDirectory = context.getRealPath("/");        //  建立Blob物件，交由 Hibernate 寫入資料庫        if (productImage != null && !productImage.isEmpty() ) {            try {                byte[] b = productImage.getBytes();                Blob blob = new SerialBlob(b);                bb.setCoverImage(blob);            } catch(Exception e) {                e.printStackTrace();                throw new RuntimeException("檔案上傳發生異常: " + e.getMessage());            }        }
```

```markup
 try {            File imageFolder = new File(rootDirectory, "images");            if (!imageFolder.exists()) imageFolder.mkdirs();            File file = new File(imageFolder, bb.getBookId() + ext);            productImage.transferTo(file);        } catch(Exception e) {            e.printStackTrace();            throw new RuntimeException("檔案上傳發生異常: " + e.getMessage());        }
```

## ajax

{% embed url="https://www.youtube.com/watch?v=12tjh\_6xL2M" %}

{% embed url="https://developer.mozilla.org/zh-TW/docs/Web/API/XMLHttpRequest/Using\_XMLHttpRequest\#%E6%8F%90%E4%BA%A4%E8%A1%A8%E5%96%AE%E8%88%87%E4%B8%8A%E5%82%B3%E6%AA%94%E6%A1%88" %}

## JAVA 分頁

{% embed url="https://www.jianshu.com/p/d108d0cd9acf" %}

## JPA

{% embed url="https://morosedog.gitlab.io/springboot-20190328-springboot14/" %}



## @Modelattribute

{% embed url="https://blog.csdn.net/u014645508/article/details/88871482" %}

## Bindingresult

{% embed url="https://blog.csdn.net/lihua5419/article/details/83418043" %}



