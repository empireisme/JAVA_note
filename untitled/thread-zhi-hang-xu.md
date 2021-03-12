# Thread 執行緒

## 直接建立物件法

```java
public class hellowworld {
	public static void main(String[] args) {
		Thread thread=new Thread() {
			@Override //在這裡按alt+/就可以選run
			public void run() {
				for(int i=0;i<10000;i++) {
					System.out.println("XDD");
				}
			}
			
		};//記得加上分號，建立物件加上分號
		thread.start();
		for(int i=0;i<1000;i++) {
			System.out.println("main");
		}
	}

}

```

這裡的run不能換名字，start\(\)也是

## 繼承類別後建立物件



