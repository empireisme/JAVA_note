# 格式化字串



```text
public class console_input {
	public static void main(String[] args) {
		System.out.printf("%s,歡迎光臨 %d%n","AdB",100);
		int i=100;
		System.out.println("total"+i);
		System.out.printf("您好，%s先生%n"
		+"消費金額一共是%d元整%n"
		+"您的紅利回饋是消費金額的%f%%","天恩",10000,1.0			
);
	}
}
```

![the result ](../../.gitbook/assets/image%20%288%29.png)

key:如果想要加入%比的話，可以加入%%\(兩個百分比\)

key:請注意是printf而非println

%s是占用符號，意思是%s放的位置之後要放字串，也就是天恩



