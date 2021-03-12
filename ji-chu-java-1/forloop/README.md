# 迴圈

## 迴圈的結構

for\(int i=? ; i&lt;=?;i++\){

}

```text
public class forloop {
	public static void main(String[] args) {
		int sum=0;
		for(int i=0;i<=100;i++) {
			sum+=i;
			System.out.println((sum-i)+"+"+i+"="+sum);
		}
	System.out.println(sum);
	
	
	
	}
}

```

tips:可在迴圈類宣告變數i



![](../../.gitbook/assets/image%20%282%29.png)

## 經典考題

試著去想想看列印出來的結果為多少

```text
public class classicforloop {
	public static void main(String[] args) {
		for(int i=0;i<3;i++) {
			switch(i) {
			case 0: break;
			case 1: System.out.print("1 ");
				break;
			case 2: System.out.print("2 ");
			case 3: System.out.print("3 ");	
		}
		System.out.print("4");
		
		
	}
}
}
```

![](../../.gitbook/assets/image%20%287%29.png)

## 九九乘法表

```text
public class ninenine {
	public static void main(String[] args) {
		for (int i=2; i<=9;i++) {
			for(int j=1; j<=9; j++) {
				System.out.printf("%dX%d=%2d\t",i,j,i*j);
				
			}
			System.out.println();
		}
	}

}

```

![](../../.gitbook/assets/image%20%285%29.png)

