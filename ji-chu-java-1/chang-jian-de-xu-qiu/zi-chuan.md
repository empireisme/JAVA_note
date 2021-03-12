# 字串

## 字串的相等

```text
package bubblesort;

public class string {
	public static void main(String[] args) {
		String str1="sdf";
		String str2="sdf";
		System.out.println(str1==str2);//true
		String str3="sdf";
		String str4= new String("sdf");
		System.out.println(str3==str4);//false compare id
		//equals比對字串值的方法
		System.out.println("asdf".length());
		System.out.println("mikes".indexOf("ki"));
		System.out.println("mikes".indexOf("ke"));
	}
	
}
```



