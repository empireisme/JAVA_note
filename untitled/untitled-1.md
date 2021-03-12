# Set

Set 集合，特色是儲存的資料沒有順序，且Set中不會有重複的元素。

```java
package day4;

import java.util.HashSet;
import java.util.Set;

public class myset {
	public static void main(String[] args) {
		Set myset=new HashSet();
		myset.add("html");
		myset.add("JAVA");
		myset.add("SQL");
		System.out.println(myset.contains("html"));
		System.out.println(myset.toString());
		System.out.println(myset.size());
		for(Object object:myset) {
			System.out.println(object);
		}// print element in myset
		
		
	}

}
```



