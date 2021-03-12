# 在預設建構子的世界中

## 物件導向OOP設計

在這個章節中，我要先以一個通俗的舉例方便讓大家知道，如果沒有方法的物件會有甚麼狀況。

**class和object並非是相同的。class是設計圖，而object是實體!**

想像你有一Class叫student，這個student是一個類別，而每個student都有爸爸\(dadname\)和成績\(score\)兩個**屬性\(attribute\)。**

\*\*\*\*

### **沒有預設值**

```java
class Student{
    public String dadname;
    public int score;
}

public class Object{
	public static void main(String[] args) {
		Student A= new Student( );\\宣告一個學生物件A
		A.dadname="mike";
		A.score=5;
		System.out.println(A.dadname);
		System.out.println(A.score);
		
	}

}



```

## 存在預設值

我們預設學生的爸爸是John，成績考50分

```java
class Student{
    public String dadname="john";
    public int score=50;
}


public class Object{
	public static void main(String[] args) {
		Student A= new Student( );
		System.out.println(A.dadname);
		System.out.println(A.score);
		
	}

}
```



## 錯誤的code

```java
class Student{
    public String dadname="sd";
    public int score=100;
    	Student( String x, int y){
    	dadname=x;
    	score=y;
   	
    }
}

class test{
	public static void main(String[] args) {
		Student A= new Student();
		System.out.println(A.dadname);
		System.out.println(A.score);
		
	}

}

```



