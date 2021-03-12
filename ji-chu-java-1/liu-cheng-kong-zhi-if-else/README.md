# 流程控制if else

```text
public class ifelse {
	public static void main(String[] args) {
		Scanner sc= new Scanner(System.in);
		int age=sc.nextInt();
		if(age>=18) System.out.println("you are a adult");
		
		sc.close();
	}
}
```

![](../../.gitbook/assets/image%20%283%29.png)

```text
public class ifelse {
	public static void main(String[] args) {
		Scanner sc= new Scanner(System.in);
		int score=sc.nextInt();
		System.out.println("grade: ");
		
		if(score>=90){System.out.println("A");}
		else if(score>80) {System.out.println("B");}
		else if(score>70) {System.out.println("C");}
		else {System.out.println("sorry can not pass");}
		
		
		sc.close();
	}
}
```



