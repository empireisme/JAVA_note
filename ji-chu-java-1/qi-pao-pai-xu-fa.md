# 氣泡排序法

要注意的是由於java陣列是傳遞參考，所以會直接改變物件的值，是故可以使用



```text
bubbleSort(arr2);
```



```text
public class BubbleSortExample {  
    static void bubbleSort(int[] arr) {  
        int n = arr.length;  
        int temp = 0;  
         for(int i=0; i < n; i++){  
                 for(int j=1; j < (n-i); j++){  
                          if(arr[j-1] > arr[j]){  
                                 //交換元素  
                                 temp = arr[j-1];  
                                 arr[j-1] = arr[j];  
                                 arr[j] = temp;  
                         }  
                          
                 }  
         }  
  
    }  
    public static void main(String[] args) {  
                int arr2[] ={3,60,35,2,45,320,5};  
                 
                System.out.println("原來的次序");  
                for(int i=0; i < arr2.length; i++){  
                        System.out.print(arr2[i] + " ");  
                }  
                System.out.println();  
                  
                bubbleSort(arr2);//利用泡沫排序
                 
                System.out.println("使用泡沫排序");  
                for(int i=0; i < arr2.length; i++){  
                        System.out.print(arr2[i] + " ");  
                }  
   
        }  
}  
```



