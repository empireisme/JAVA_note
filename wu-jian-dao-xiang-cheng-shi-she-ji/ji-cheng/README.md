# 繼承

繼承是一種可以省下程式碼的事情

```text
package day5test;

public class car {
	private int speed;
	private int oil;
	public car(int speed, int oil) {
		super();
		this.setSpeed(speed);
		this.setOil(oil);
	}
	public car() {
	}
	public int getSpeed() {
		return speed;
	}
	public void setSpeed(int speed) {
		this.speed = speed;
	}
	public int getOil() {
		return oil;
	}
	public void setOil(int oil) {
		this.oil = oil;
	}
	
}
```

```text
package day5test;

public class taxi extends car{
	int unitcost=25;
	int initial=70;
	//計程車要限速度
	public void setSpeed(int speed) {
		if(speed>80||speed<0) {
		System.out.println("不行這樣開");
		}else {
			super.setSpeed(speed);//使用父類別
		}

	}
	public int getPrice(int time) {
		int price=initial+time*getSpeed()*unitcost;
		return price;
	}
}
```

```text
package day5test;

public class taxidemo {
	public static void main(String[] args) {
		taxi mike=new taxi();
		mike.setSpeed(100);
		mike.getOil();
		System.out.println("共計"+mike.getPrice(3)+"元");
	}
}
```

