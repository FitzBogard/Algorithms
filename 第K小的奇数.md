查找数组arr中第k小的奇数,如果不存在则返回0. (arr[i] > 0 (i>=0))  
计算出时间复杂度（注意代码注释，尽可能不用全排序，不要使⽤库函数或脚本中已经实现好的排序算法和⼯具, 需要⾃⼰实现数据结构和所需要的算法）  
```java
//全排序算法例如冒泡、插入、快速排序，这些都是对整个数组进行排序，即使时间复杂度有优化但不符合题设。
public class Solution {
    public int findKth(int[] arr,int k) {
        //对arr插入排序
        for(int i = 1; i < arr.length; i++) {
            int tmp = arr[i];
            int j = i - 1;
            while(j>=0 && tmp < arr[j]) {
                arr[j+1] = arr[j];
                j--;
            }
            arr[j+1] = tmp;
        }

        //判断是否为奇数，用一个int变量来记录奇数出现的次数。
        int cnt = 0;
        for(int i=0;i<arr.length;i++) {
            if(arr[i] % 2 != 0) {
                cnt++;
            }
            if(cnt == k) {
                return arr[i];
            }
        }
        return 0;
    }
}
```
```java
//可以先把奇数找出来 判断是否大于K个 如果大于K个再全排序，但是依旧是使用了全排序，这里使用一个相当于小顶堆的优先队列
public static int findKth2(int[] arr, int k) {
    PriorityQueue<Integer> q = new PriorityQueue<Integer>(k);
        for (int i = 0; i <arr.length ; i++) {
            if (arr[i]%2==1){   //奇数
                q.add(arr[i]);
            }
            if (q.size()>k){   //如果队列容量超过k了  就弹出最小元素
                q.poll();
            }
        }
        //判断队列长度是否为空或者根本不存在第k大的奇数
        if (q.size()!=k||q.size()==0){
            return 0;
        }else {
            return q.peek();
        }
    }

```
