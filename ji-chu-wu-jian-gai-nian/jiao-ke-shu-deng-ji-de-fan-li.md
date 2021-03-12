# 教科書等級的範例

先上code之後慢慢分析

```java
class Student{
    public String dadname="john";
    public int score=50;
    Student( String x, int y){
    	dadname=x;
    	score=y;
    }
    Student(){};//務必要加上
}
public class Object{
	public static void main(String[] args) {
		Student A= new Student(   );
		System.out.println(A.dadname);
		System.out.println(A.score);
		Student B= new Student("Mike" ,80  );
		System.out.println(B.dadname);
		System.out.println(B.score);
	}
}
```

![](../.gitbook/assets/image%20%2810%29.png)



