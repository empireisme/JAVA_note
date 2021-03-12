# Thread 執行緒

## 一樣先看範例

```java
package finalDemo;

public class hellowworld {
	public static void main(String[] args) {
		Thread thread=new Thread() {
			@Override //在這裡按alt+/就可以選run
			public void run() {
				System.out.println("XDD");
			}
			
		};//記得加上分號，建立物件加上分號
		thread.start();
		
	}

}
```



