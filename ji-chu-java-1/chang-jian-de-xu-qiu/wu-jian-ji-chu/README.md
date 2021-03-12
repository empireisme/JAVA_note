# 陣列的基礎

## **去看物件是不是一樣的**

```text
package day5;

public class Objectpractice {
	public static void main(String[] args) {
		Object o1=new Object();
		Object o2=new Object();
		Object o3=o1;
		//Object 內建的物件，裡面有物件最基本的特性，
		//他可以包玵所有種類的物件
		System.out.println(o1==o2);//false
		System.err.println(o1==o3);//True
		System.out.println(o2==o3);//false
	}
}
```

## **宣告物件陣列**

```text
public class day1_4 {
	public static void main(String[] args) {
		int [] intarr=new int[3];
		animal[] arr=new animal[3];//put 3 animals in arr
		//陣列都是物件
		arr[0]=new animal();
		arr[1]=new animal();
		arr[2]=new animal();
		arr[0].name="sam";
		arr[0].high=120;
		arr[0].weight=5;
		
	}
}
```

## **宣告2 dim 陣列**

```text
public class day1_5 {
	public static void main(String[] args) {
		int[][] arr=new int[3][];//可以只要宣告前面的數字
		arr[0]=new int[10];//可以存10個int
		arr[1]=new int[8];//可以存8個int
		arr[2]=new int[2];//可以存2個int
		//中間東西數量不固定
		
	}
}
```

## **提取2 dim 陣列**

```text
public class day1_5 {
	public static void main(String[] args) {
		int[][] arr=new int[3][];//可以只要宣告前面的數字
		int[][ ]arr2= {{1,20,23} ,{3,5,6},{2,5,22}};
		arr[0]=new int[10];//可以存10個int
		arr[1]=new int[8];//可以存8個int
		arr[2]=new int[2];//可以存2個int
		int[ ]arr1=arr2[2];//{2,5,22}
		for (int i = 0; i < arr1.length; i++) {
			System.out.println(arr1[i]);
			
		}
		//2,5,22
		//中間東西數量不固定
		
	}
}

```

## 2 dim array for each

```java
public class day1_5 {
	public static void main(String[] args) {
		int[][] arr=new int[3][];//可以只要宣告前面的數字
		int[][ ]arr2= {{1,20,23} ,{3,5,6},{2,5,22}};

		for (int[] is : arr2) {
			for(int i : is) {
				System.out.println(i);
			
			}
		}
		//2,5,22
		//中間東西數量不固定
		
	}
}
```

{% hint style="info" %}
請注意要使用



```java
	for (int[] is : arr2) {
			for(int i : is) {
				System.out.println(i);
			
			}
		}
```
{% endhint %}

## 物件陣列

```text
package day5;
//Object and basic data type
public class day1_6 {
	public static void main(String[] args) {
		int[] arr1=new int[3];//整數陣列
		animal []arr2=new animal[3];//物件陣列
		arr1[0]=1;
		arr1[1]=2;
		arr1[2]=3;
		arr2[0]= new animal();
		arr2[0].name="阿A";
		arr2[1]= new animal();
		arr2[1].name="阿B";
		arr2[2]= new animal();
		arr2[2].name="阿C";
		
				
	}
}
```

## For each 針對物件和針對基本資料型別會不一樣的結果

```text
package day5;
//Object and basic data type
public class day1_6 {
	public static void main(String[] args) {
		int[] arr1=new int[3];//整數陣列
		animal []arr2=new animal[3];//物件陣列
		
		arr1[0]=1;
		arr1[1]=2;
		arr1[2]=3;
		
		arr2[0]= new animal();
		arr2[1]= new animal();
		arr2[2]= new animal();
		
		arr2[0].name="阿A";
		arr2[1].name="阿B";
		arr2[2].name="阿C";
		
		for(int i:arr1) {
			i=9;
		}
		for(animal element:arr2) {
			element.name="阿D";
		}
		for(int i:arr1) {
			System.out.println(i);
		}//print 1,2,3
		for(animal element:arr2) {
			System.out.println(element.name);
		}
		//print 阿D 阿D 阿D
	}
}

```

## 矩陣的轉至矩陣

```text
public class day1_7 {
	public static void main(String[] args) {
		int[][]arr= { {1,2}, {3,4} ,{5,6} , {7,8}};
		int[][]arrans=new int[2][4];
//		System.out.println(arrans.length);
		for(int i=0;i<arrans.length;i++) {
			for(int j = 0; j < arrans[i].length; j++) {
				arrans[i][j]=arr[j][i];
			}	
		}
		
		for(int i=0;i<arrans.length;i++) {
			for(int j = 0; j < arrans[i].length; j++) {
				System.out.print(arrans[i][j]+" ");
			}
			System.out.println();
		}
	}
}
```

