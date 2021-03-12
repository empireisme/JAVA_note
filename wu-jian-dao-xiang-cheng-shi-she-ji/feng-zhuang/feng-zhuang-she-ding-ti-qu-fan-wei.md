# 封裝\_設定提取範圍

問題描述:你想要對設定的身高給予一個合理的範圍，若輸入的數字不合理，那就跳出錯誤訊息，合理的化存進去。



```text
package day5test;

public class human {
	private int height;
	private int weight;
	public int getHeight() {
		return height;
	}
	public void setHeight(int height){
		
		if(height<200&height>100) {
			this.height = height;
		}else {
		System.out.println("高度錯誤");
		this.height=height=150;
		}
	}
	public int getWeight() {
		return weight;
	}
	public void setWeight(int weight) {
		this.weight = weight;
	}
}
```

```text
package day5test;

public class humandemo {
	public static void main(String[] args) {
		human mike=new human();
		mike.setHeight(26);
		System.out.println(mike.getHeight());
		mike.setHeight(180);
		System.out.println(mike.getHeight());
	}
}
```

