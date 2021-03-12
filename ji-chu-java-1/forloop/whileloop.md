# whileloop

{% tabs %}
{% tab title="Java" %}
```java
public class whileloop {
	public static void main(String[] args) {
		int i=1;
		while(i<99) {
			i+=1;
			System.out.println(i);
		}
	}
}


```
{% endtab %}

{% tab title="" %}
```

```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
請注意宣告i 要擺在外面!!!!!

結束條件i=99擺在while\(\)

內容物裡面擺上跌代條件
{% endhint %}

## 永遠回應你輸入的字串的code

```java
public class whileloop {
	public static void main(String[] args) {
		Scanner sc= new Scanner(System.in);
		boolean  main_switch=true;
		while(main_switch) {
			String str1=sc.nextLine();
			switch (str1) {
			case "exit":
				System.out.println("close");
				main_switch=false;
				break;
			default:
				System.out.println(str1);
				break;
			
			}
		}
		
		
		sc.close();
	}
}
```



