# 方法

## 1.把方法寫在和main同一個class裡面

```java
package day5;

public class day1_8 {
	public static int add(int a,int b) {
		int c;
		c=a+b;
		return c;
	}
	
	public static void main(String[] args) {
		int total;
		total=add(5,3);
		System.out.println(total);
	}

}
```

注意這個寫法需要加上static

## 2.把方法放在其他class裡面，需宣告物件或是使用static修飾

```java
package day5;

public class demo1 {
	static int abcd;
	public static int add(int a,int b) {
		int c=a+b;
		return c;
	}
	public  void name(String str) {
		System.out.println(str);
		System.out.println(abcd);
	}
	public static void printhelloworld() {
		System.out.println("helloworld");
	}
	public static double BMI(double height,double weight) {
		double result=weight/height/height;
		return result;
	}
}
```

```java
package day5;

public class demomain {
	public static void main(String[] args) {
		demo1.printhelloworld();
		demo1.add(10,11);
//		demo1.name("asdf");//name方法沒有被宣告為static 故不能使用
		demo1 d1=new demo1();
		int total;
		total=d1.add(10,11);
		System.out.println(total);
		d1.name("Mike");
		double result=demo1.BMI(1.75,90 );
		System.out.println(result);
		System.out.println(demo1.BMI(1.75,90 ));
	}
}

```

