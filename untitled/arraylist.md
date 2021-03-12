# Arraylist

## Arraylist的宣告與一般常見操作

```java
package day4;

import java.util.List;
import java.util.ArrayList;

public class List_demo {
	public static void main(String[] args) {
		//int[ ] arr=new int[8];
		//空間固定
		String s1="java";
		String s2="SQL";
		String s3="html";
		String s22="a";
		List list=new ArrayList();
		list.add(s1);//添加物見到arraylist
		list.add(s2);//添加物見到arraylist
		list.add(s3);//添加物見到arraylist
		list.add(0,s22);//添加物建到指定的index，會往後推移
		list.remove(s3);
		System.out.println(list.get(0));
		for(int i=0;i<list.size();i++) {
			System.out.println(list.get(i));
		}
	}

}
```

