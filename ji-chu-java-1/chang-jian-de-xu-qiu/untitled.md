# 從鍵盤輸入

```text
public class input {
	public static void main(String[] args) {
	Scanner sc=new Scanner(System.in);//宣告Scanner
	String  myname=sc.next();//讀取到下一個標誌的位置。
	String  mypoint=sc.next();可以輸入帶有空白的字串
	System.out.printf("您好，%s先生%n"
			+"消費金額一共是%d元整%n"
			+"您的紅利回饋是消費金額的%1.4fd%%%n",myname,Integer.parseInt(mycost),
			Double.parseDouble(mypoint));
	}
}
```

![](../../.gitbook/assets/image%20%284%29.png)

