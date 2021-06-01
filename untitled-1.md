# 專題會用到的技術

![](.gitbook/assets/image%20%28125%29.png)

![](.gitbook/assets/image%20%28124%29.png)

## 專題技術連結

{% embed url="https://ithelp.ithome.com.tw/articles/10247242" %}

![](.gitbook/assets/image%20%28128%29.png)

{% embed url="https://medium.com/chikuwa-tech-study/%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B-%E4%BD%87%E5%88%97-queue-673c8c33ee4c" %}

{% embed url="https://medium.com/chikuwa-tech-study/tagged/spring-boot" %}

{% embed url="https://ithelp.ithome.com.tw/articles/10194425" %}

## JSP表格

{% embed url="https://stackoverflow.com/questions/43398579/how-to-display-string-of-json-in-jsp-table" %}

## 註冊帳號的範例jSP

```markup
<%@ page language="java" contentType="text/html; charset=UTF-8"
	pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>	
<!DOCTYPE html>
<html>
<head>
<script>
var hasError = false;
window.onload = function() {
	var alink = document.getElementById("accountCheck");
	var div = document.getElementById('result0c');
	alink.onclick = function() {
	  var idValue = document.getElementById("id").value;
	  if (!idValue) {
		div.innerHTML = "<font color='blue' size='-1'>請輸入帳號...</font>";
		return;
	  }
	  var xhr = new XMLHttpRequest();
	  xhr.open("POST", "<c:url value='/_02/CheckMemberId' />", true);
	  xhr.setRequestHeader("Content-Type",
				"application/x-www-form-urlencoded");
	  xhr.send("id=" + idValue);
	  var message = "";
	  xhr.onreadystatechange = function() {
	    // 伺服器請求完成
	    if (xhr.readyState == 4 && xhr.status == 200) {
		   var result = JSON.parse(xhr.responseText);
		   if (result.id.length == 0) {
			  message = "<font color='green' size='-2'>帳號可用</font>";
		   } else if (	result.id.startsWith("Error") ) {
			  message = "<font color='red' size='-2'>發生錯誤: 代號" + result.id + "</font>";
		   } else {
			  message = "<font color='red' size='-2'>帳號重複，請重新輸入帳號</font>"; 
		   }
		   div.innerHTML = message;
	    }
     }
   }
   var sendData = document.getElementById("sendData");
   sendData.onclick = function() {
		hasError = false;
   		// 讀取欄位資料	  
		var idValue = document.getElementById("id").value;
		var nameValue = document.getElementById("name").value;
		var balanceValue = document.getElementById("balance").value;
		var birthdayValue = document.getElementById("birthday").value;
		var div0 = document.getElementById('result0c');
		var div1 = document.getElementById('result1c');
		var div2 = document.getElementById('result2c');
		var div3 = document.getElementById('result3c');
		var divResult = document.getElementById('resultMsg');
		if (!idValue){
			setErrorFor(div0, "請輸入帳號");
   		} 	else {
      		div0.innerHTML = "";
   		}
		if (!nameValue){
			setErrorFor(div1, "請輸入姓名");
		} else {
			div1.innerHTML = "";
		}
   		if (!balanceValue){
			setErrorFor(div2, "請輸入餘額");
		} else {
	   		var objRegex = /^\d+$|(^-?\d\d*\.\d\d*$)|(^-?\.\d\d*$)/;  
			if(!objRegex.test(balanceValue))    {  
				setErrorFor(div2, "餘額欄必須是數值");
       		} else { 
           		div2.innerHTML = "";
       		}
   		}
   		if (!birthdayValue){
			setErrorFor(div3, "請輸入生日");  
   		} else if(!dateValidation(birthdayValue)) {
			setErrorFor(div3, "生日格式錯誤，正確格式為yyyy-MM-dd");
   		} else {
       		div3.innerHTML = "";
   		}
   		if (hasError){
       		return false;
   		}
   		var xhr1 = new XMLHttpRequest();
   		xhr1.open("POST", "<c:url value='/members' />", true);
		var jsonMember = {
			"id": idValue, 	
			"name": nameValue,
			"balance": balanceValue,
			"birthday": birthdayValue
   		}
  		xhr1.setRequestHeader("Content-Type", "application/json");
  		xhr1.send(JSON.stringify(jsonMember));
//      以下敘述錯誤  		
// 		xhr1.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
//    		xhr1.send("id=" + idValue + "&name=" + nameValue + "&balance=" 
//    				+ balanceValue + "&birthday=" + birthdayValue );
   
   		xhr1.onreadystatechange = function() {
				// 伺服器請求完成
   		if (xhr1.readyState == 4 && (xhr1.status == 200 || xhr1.status == 201) ) {
      		result = JSON.parse(xhr1.responseText);
      		if (result.fail) {
		 		divResult.innerHTML = "<font color='red' >"
					+ result.fail + "</font>";
	  		} else if (result.success) {
				divResult.innerHTML = "<font color='GREEN'>"
					+ result.success + "</font>";
				div0.innerHTML = "";	
				div1.innerHTML = "";
				div2.innerHTML = "";
				div3.innerHTML = "";
	 		} else {
				if (result.idError) {
          			div0.innerHTML = "<font color='green' size='-2'>"
	     				+ result.idError + "</font>";
				} else {
          			div0.innerHTML = "";
				}
				if (result.nameError) {
	      			div1.innerHTML = "<font color='green' size='-2'>"
						+ result.nameError + "</font>";
				} else {
	      			div1.innerHTML = "";
	   			}
				if (result.balanceError) {
          			div2.innerHTML = "<font color='green' size='-2'>"
						+ result.balanceError + "</font>";
				} else {
          			div2.innerHTML = "";
    			}
				if (result.birthdayError) {
	    			div3.innerHTML = "<font color='green' size='-2'>"
						+ result.birthdayError + "</font>";
				} else {
          			div3.innerHTML = "";
				}
      		}
		} 
  	    }
    }
		
}

function setErrorFor(input, message){
	input.innerHTML = "<font color='red' size='-2'>" + message + "</font>";
    hasError = true;
}

function dateValidation(str) {
	  var re = new RegExp("^([0-9]{4})[.-]{1}([0-9]{1,2})[.-]{1}([0-9]{1,2})$");
	  var days = [0, 31, 28, 31, 30,  31, 30, 31, 31, 30, 31, 30, 31];
	  var strDataValue;
	  var valid = true;
	  if ((strDataValue = re.exec(str)) != null) {
	    var y, m, d;
	    y = parseFloat(strDataValue[1]);
	    if (y <= 0 || y > 9999) { /*年*/
	      return false;
	    } 
	    m = parseFloat(strDataValue[2]);
	    
	    if (m < 1 || m > 12) { /*月*/
	        return false;
	    }
	    d = parseFloat(strDataValue[3]);
	    if ( y % 4 == 0 && y % 100 != 0 || y % 400 == 0 ){
	       days[2] = 29;
	    }  else {
	       days[2] = 28;
	    }
	    if (d <= 0 || d > days[m]) { /*日*/
	      valid = false;
	    }
	  } else {
	    valid = false;
	  }  
	  return valid;
	}

	function isEmail(email) {
		return /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(email);
	}

</script>
<link rel='stylesheet' href="<c:url value='/css/styles.css' />" type="text/css" />	
<meta charset="UTF-8">
<title>Registration</title>
</head>
<body>
<div align='center'>
<h3>輸入會員資料</h3>
<hr>
<div id='resultMsg' style="height: 18px; font-weight: bold;"></div>
	<br>
	<fieldset style='display: inline-block; width: 820px;'> 
	<legend>填寫下列資料</legend>
	<table border='1'>
	<tr height='60'>
		<td width='200'>&nbsp;</td>
		<td width='400'>
			&nbsp;帳號: <input type="text" name="id" id='id'><br>
			<div style='font-size: 10pt; text-align: center;'>
   				<a href='#' id='accountCheck' style='font-size: 10pt;'>檢查帳號</a>
			</div>
		</td>
		<td width='200'>
			<div id='result0c' style="height: 10px;"></div><br>
			<div id='result0s' style="height: 10px;"></div>
		</td>
	</tr>
	<tr height='60'>
		<td width='200'>&nbsp;</td>
		<td width='400'>
			&nbsp;姓名: <input type="text" name="name" id='name'><br>
		</td>
		<td width='200' style="vertical-align:top">
			<div id='result1c' style="height: 10px;"></div><br>
			<div id='result1s' style="height: 10px;"></div>
		</td>	
	</tr>
	<tr height='60'>
		<td width='200'>&nbsp;</td>
		<td width='400'>
			&nbsp;餘額: <input type="text" name="balance" id='balance'><br>
		</td>
		<td width='200' style="vertical-align:top">
			<div id='result2c' style="height: 10px;"></div><br>
			<div id='result2s' style="height: 10px;"></div>
		</td>	
	</tr>
	<tr height='60'>		
		<td width='200'>&nbsp;</td>
		<td width='400'>
			&nbsp;生日: <input type="text" name="birthday" id='birthday' size='24'>
		</td>	
		<td width='200'>
			<div id='result3c' style="height: 10px;"></div><br>
			<div id='result3s' style="height: 10px;"></div>			
		</td>	
	</tr>
	<tr height='50'>		
		<td colspan='3' align='center'><button id='sendData'>送出</button></td>
	</tr>		
			</table>
		</fieldset>
	<hr>	
	<p>	
	<a href="<c:url value='/index'  />">回前頁</a>
<hr>
</div>

</body>
</html>
```

## 一進去就看到所有表單

showAllmembers

```markup
<%@ page language="java" contentType="text/html; charset=UTF-8"
	pageEncoding="UTF-8"%>
<%@ taglib prefix='c' uri='http://java.sun.com/jsp/jstl/core' %>
<%@ taglib prefix='fmt' uri="http://java.sun.com/jsp/jstl/fmt" %>
<!DOCTYPE html>
<html>
<head>
<link rel='stylesheet' href="<c:url value='/css/styles.css' />" type="text/css" />
<meta charset="UTF-8">
<title>會員資料</title>
<script type="text/javascript" src="<c:url value='/js/jquery-1.12.2.min.js' />" ></script>


<script>
window.onload = function() {
	var xhr = new XMLHttpRequest();
	xhr.open("GET", "<c:url value='/members' />", true);
	xhr.send();
	xhr.onreadystatechange = function() {
		if (xhr.readyState == 4 && xhr.status == 200) {
			var content = "<table border='1'>";
			content += "<tr><th width='80'>編輯</th><th width='100'>帳號</th><th width='180'>姓名</th><th width='90'>餘額</th><th width='140'>生日</th></tr>";
			var members = JSON.parse(xhr.responseText);
			for(var i=0; i < members.length; i++){
				tmp = "<c:url value='/membersEdit/' />";
			    content += 	"<tr><td width='70'><a href='" + tmp + members[i].pk + "'>" + 
			    			"<img width='36' height='36' src='<c:url value='/images/edit.png' />' ></a>" + 
			                "<td align='center'>" + members[i].id + "</td>" +
		        	       	"<td>" + members[i].name + "</td>" +
		            	   	"<td align='right'>" + members[i].balance + "&nbsp;</td>" +
							"<td>" + members[i].birthday + "</td>" +
		               		"</tr>";
			}
			content += "</table>";
			var divs = document.getElementById("somedivS");
			divs.innerHTML = content;
		}
	}
		
}
</script>
</head>
<body>
<div class='center' >
	<h2>會員資料</h2>
	<hr>
	<div class='center'  id='somedivS'></div>
	</div>
</body>
	
<p/>
<div align='center'>
<a href="<c:url value='/index/' />">回前頁</a>
</div>
</body>
</html>

```

## 上一頁下一夜JSP

```markup
<%@ page language="java" contentType="text/html; charset=UTF-8"
	pageEncoding="utf-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<link rel='stylesheet' href="<c:url value='/css/styles.css' />" type="text/css" />	
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
<script type="text/javascript" src="<c:url value='/js/jquery-1.12.2.min.js' />"></script>
<script>  
	window.onload = function() {
		var books;
// 		var btn = document.getElementById("clickmeS"); // 『Click Me(JavaScript)』按鈕的事件處理函數
		var xhr = new XMLHttpRequest(); 
		xhr.open("GET", "<c:url value='/ch04/_07/pagingBookData.json'/>", true);
		                              
			              
			xhr.send();
			xhr.onreadystatechange = function() {
				if (xhr.readyState == 4 && xhr.status == 200) {
					var content = "<table border='1'>";
					content += "<tr><th>編號</th><th>書名</th><th>作者</th><th>價格</th>" 
							 + "<th>出版社</th><th>封面</th></tr>";
					books = JSON.parse(xhr.responseText);
					var imageURL = "<c:url value='/ch04/_03/getBookImage' />";
					for (var i = 0; i < books.list.length; i++) {
						content += "<tr><td align='center'>" + books.list[i].bookId + "</td>" 
								+ "<td>" + books.list[i].title + "</td>"
								+ "<td>" + books.list[i].author + "</td>"
								+ "<td align='right'>" + books.list[i].price + "</td>" 
								+ "<td align='center'>"	+ books.list[i].publisherBean.name.substring(0, 2)
								+ "</td>" + "<td><img  width='40' height='48' "
								+ " src='" + imageURL + "?no="  
								+ books.list[i].bookId + "'></td></tr>";
						
					}
					content += "</table>";
					var divs = document.getElementById("somedivS");
					divs.innerHTML = content;
				}
			}
	
	
	var btnbefore = document.getElementById("before"); 
	btnbefore.onclick = function() {
		var xhr = new XMLHttpRequest();
		var beforepage = books.currPage-1;
		xhr.open("GET", "<c:url value='/ch04/_07/pagingBookData.json'/>"+"?pageNo="+beforepage, true);
		
		              
		xhr.send();
		xhr.onreadystatechange = function() {
			if (xhr.readyState == 4 && xhr.status == 200) {
				var content = "<table border='1'>";
				content += "<tr><th>編號</th><th>書名</th><th>作者</th><th>價格</th>" 
						 + "<th>出版社</th><th>封面</th></tr>";
				 books = JSON.parse(xhr.responseText);
				var imageURL = "<c:url value='/ch04/_03/getBookImage' />";
				for (var i = 0; i < books.list.length; i++) {
					content += "<tr><td align='center'>" + books.list[i].bookId + "</td>" 
							+ "<td>" + books.list[i].title + "</td>"
							+ "<td>" + books.list[i].author + "</td>"
							+ "<td align='right'>" + books.list[i].price + "</td>" 
							+ "<td align='center'>"	+ books.list[i].publisherBean.name.substring(0, 2)
							+ "</td>" + "<td><img  width='40' height='48' "
							+ " src='" + imageURL + "?no="  
							+ books.list[i].bookId + "'></td></tr>";
					
				}
				content += "</table>";
				var divs = document.getElementById("somedivS");
				divs.innerHTML = content;
				if(books.currPage==1){
					before.style="visibility:hidden"

				}
				if(books.currPage<books.totalPage){
					after.style="visibility:none"

				}
			}
		}
	}
	

	var btnafter = document.getElementById("after"); 
	btnafter.onclick = function() {
		var xhr = new XMLHttpRequest();
		var afterpage = books.currPage+1;
		xhr.open("GET", "<c:url value='/ch04/_07/pagingBookData.json'/>"+"?pageNo="+afterpage, true);
		
		              
		xhr.send();
		xhr.onreadystatechange = function() {
			if (xhr.readyState == 4 && xhr.status == 200) {
				var content = "<table border='1'>";
				content += "<tr><th>編號</th><th>書名</th><th>作者</th><th>價格</th>" 
						 + "<th>出版社</th><th>封面</th></tr>";
				 books = JSON.parse(xhr.responseText);
				var imageURL = "<c:url value='/ch04/_03/getBookImage' />";
				for (var i = 0; i < books.list.length; i++) {
					content += "<tr><td align='center'>" + books.list[i].bookId + "</td>" 
							+ "<td>" + books.list[i].title + "</td>"
							+ "<td>" + books.list[i].author + "</td>"
							+ "<td align='right'>" + books.list[i].price + "</td>" 
							+ "<td align='center'>"	+ books.list[i].publisherBean.name.substring(0, 2)
							+ "</td>" + "<td><img  width='40' height='48' "
							+ " src='" + imageURL + "?no="  
							+ books.list[i].bookId + "'></td></tr>";
					
				}
				content += "</table>";
				var divs = document.getElementById("somedivS");
				divs.innerHTML = content;
				
				before.style="visibility:none"
				
				if(books.currPage==books.totalPage){
					after.style="visibility:hidden"
				}
			}
		}
	}
	
	
	
	
	
	}
	
	
</script>
</head>
<body>
	<div align='center'>
		<h3>顯示所有書籍資料(JSON)</h3>
		<hr>
		
		<p />
<!-- 		<button id='clickmeS'>Click Me(JavaScript)</button> -->
		<button id='before' style="visibility:hidden"  >before </button>
		<button id='after'>after</button>
		<hr>
		<div id='somedivS'></div>
		<hr>
		<a href="<c:url value='/ch04/' />">回前頁</a>
	</div>
</body>
</html>
```

