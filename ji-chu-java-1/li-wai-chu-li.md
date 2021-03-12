# 例外處理

一個超級經典的例子

```text
import java.util.Scanner;

public class compute {
	public static void main(String[] args) {
		Scanner sc=null;
		try {
			sc=new Scanner(System.in);
			int a=sc.nextInt();
			int b=sc.nextInt();
			System.out.println(a/b);
		}catch(Exception e){
			System.out.println("出事了");
			System.out.println(e);//印出error方便debug
			e.printStackTrace();
			System.out.println(e.getClass().getSimpleName());
		}finally {
			if (sc!=null) {
				sc.close();
			
			}	
			System.out.println("finally區");
		}
		System.out.println("計算完畢");
	}
}

```



