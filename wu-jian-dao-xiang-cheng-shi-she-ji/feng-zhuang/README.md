---
description: 精神在於有些屬性或是方法可以由class設計者決定要不要給人使用
---

# 封裝

## 點運算子的世界

照慣例，先來看一段code

```text
public class Bank_account {
	public int money=100;
	public int year=3;
	public double rate=0.2;
	public Bank_account(int money, int year, float rate) {
		this.money = money;
		this.year = year;
		this.rate = rate;
	}
	public Bank_account() {
	}

}
```

```text
public class Bank_main {
	public static void main(String[] args) {
		Bank_account mike=new Bank_account();
		mike.money=500;
		System.out.println(mike.money);//
		
	}
}
```



