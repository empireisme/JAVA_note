# 字串物件的雷坑

```text
public class three {
	public static void main(String[] args) {
		String i="A";
		String j=i;
		System.out.println(i==j);
		
	    s= new String("A");//字串物件建立
		System.out.println("A"==s);//meory location// no
		System.out.println(s);
		
		}
		
```

