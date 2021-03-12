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

```java
public class noarm extends Thread {
	public void name() {
		System.out.println("V");
	}
	public void run() {
		super.run();
		for(int i=0;i<10000;i++) {
			name();
		}
	}

}
```

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
		
		Thread th2=new noarm();
		
		thread.start();
		th2.start();
		for(int i=0;i<1000;i++) {
			System.out.println("main");
		}
	}

}
```

```java
public class hihi {
	public static void main(String[] args) {
		Thread th1=new Thread() {
			public void run() {
				Thread	t=Thread.currentThread();
				try {
					Thread.sleep(10000);
				}catch(Exception e) {
					e.printStackTrace();
				}
				System.out.println("Thread1="+t.getName());
			};
		};
//		Thread th2=new Thread() {
//			public void run() {
//				Thread	t=Thread.currentThread();
//				System.out.println("Thread2="+t.getName());
//			};
//		};
		
		
		th1.start();
		System.out.println(th1.isAlive());
		try {
			th1.join();
		}catch(Exception e) {
			e.printStackTrace();
		}
//		th2.start();
		
		Thread t=Thread.currentThread();
		System.out.println("Main="+t.getName());
		System.out.println(th1.isAlive());//此時他才死了
	}

}

```

![](../.gitbook/assets/image%20%289%29.png)

