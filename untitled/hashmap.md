# Hashmap

| 方法 | 回傳 | 功能 |
| :--- | :--- | :--- |
| put\(key,value\) | null or object |  |

```java
package day4;

import java.util.HashMap;
import java.util.Map;
import java.util.Map.Entry;
import java.util.Set;

public class mapdemo {
		public static void main(String[] args) {
			String key1="mycar";
			String key2="yourcar";
			car car1=new car();
			car car2=new car();
			Map mymap=new HashMap();
			mymap.put(key1, car1);
			mymap.put(key2, car2);
//			Object car2=mymap.get(key1);
//			if(car2 instanceof car) {
//				System.out.println("有車");
//			}else {
//				System.out.println("沒有車");
//			}
			System.out.println(mymap.get("yourcar"));
			System.out.println(mymap.get(key1));
			Set keys=mymap.keySet();
			
			for(Object object : keys) {
				
				System.out.println("key="+object+",value="
				+mymap.get(object));
			}
			Set entry=mymap.entrySet();
			System.out.println("------------");
			for (Object object : entry) {
				Entry e=(Entry) object;
				System.out.println("key="+e.getKey()+
				",value="+e.getValue());
			}
			
		}

}
```



