# JAVA IO

## JAVA IO

```java
package day5;

import java.io.File;
import java.io.FileInputStream;
import java.nio.charset.StandardCharsets;

public class fileinputdemo {
	public static void main(String[] args) {
		try {
			String filepath="c:/cmp/a.txt";//第一步檔案位置
			File file=new File(filepath);//利用檔案位置建立file物件
			FileInputStream fInputStream;
			fInputStream=new FileInputStream(file); //打開輸入物件
			//準備水桶
			int size=fInputStream.available();//取得檔案剩下多少位元沒有讀取
			byte[] b=new byte[size];
			
			fInputStream.read(b);//讀資料
			
			String f =new String(b,StandardCharsets.UTF_8);
			//byte陣列轉入文字，解析完變成字串
			System.out.println(f);//印出字串
			fInputStream.close();
		}catch( Exception e){
			
		}
		
		
		
	}
}
```

## 改寫TRY成try with resource

好處是可以不用寫close

```java
public class fileinputdemo2 {
	public static void main(String[] args) {
		String filepath="c:/cmp/a.txt";//第一步檔案位置
		File file=new File(filepath);//利用檔案位置建立file物件
		
		try(FileInputStream fInputStream=new FileInputStream(file)) {
			
			int size=fInputStream.available();//取得檔案剩下多少位元沒有讀取
			byte[] b=new byte[size];
			
			fInputStream.read(b);//讀資料
			
			String f =new String(b,StandardCharsets.UTF_8);
			//byte陣列轉入文字，解析完變成字串
			System.out.println(f);//印出字串
			fInputStream.close();
		}catch( Exception e){
			e.printStackTrace();
		}
		
		
		
	}
}
```

關鍵在把FileInputStream fInputStream=new FileInputStream\(file\)移動到try\(\)括號裡面~

try catch 寫出多種錯誤訊息的好處是城市不是只給developer用，也給user用，所以需要分門別類用catch，不可以全都印

## Buffer的作法

```java
import java.io.BufferedInputStream;
import java.io.File;
import java.io.FileInputStream;
import java.nio.charset.StandardCharsets;


public class bufferinputsteamdemo {
	public static void main(String[] args) {
		
		try {
			String filepath="c:/cmp/a.txt";//第一步檔案位置
			File file=new File(filepath);//利用檔案位置建立file物件
			FileInputStream fInputStream;
			fInputStream=new FileInputStream(file);
			BufferedInputStream bis=new BufferedInputStream(fInputStream);
			

			byte[] b=new byte[fInputStream.available()];
			int i=0;
			int k=0;
			while( (i=bis.read())!=-1 ) {
				b[k]=(byte) i;
				k++;
			}
			
			System.out.println(new String(b,StandardCharsets.UTF_8));
			bis.close();
			fInputStream.close();
			
		}catch( Exception e){
			e.printStackTrace();
		}
	}
}
```







