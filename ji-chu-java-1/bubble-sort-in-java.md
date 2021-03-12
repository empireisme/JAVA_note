# 泡沫排序法

```text
public class bubblesort {
	public static void main(String[] args) {
		int[] score = {99, 3500,85, 55, 94, 77,1000};
		int len=score.length;
		for (int element: score) {
	            System.out.print(element+" ");
	        }
		
		int temp;
		for(int i=0;i<len-1;i++) {
			
			for(int j=0;j<len-1;j++) {// use len-1 take care
				if(score[j]>score[j+1]) {
				temp=score[j];
				score[j]=score[j+1];
				score[j+1]=temp;
				}
			}
		}

		System.out.println("\nprint the max number in score");
		System.out.println(score[len-1]);
		for (int element: score) {
            System.out.print(element+" ");
        }
	}
}
```

