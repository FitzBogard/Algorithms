实现 int sqrt(int x) 函数。
计算并返回 x 的平方根，其中 x 是非负整数。
由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。  
来源：力扣 #69  
- 典型的二分查找，每次让min+max / 2的值平方，和x比较大小。  
```java
class Solution {
    public int mySqrt(int x) {
        if(x == 1)  return x;
        int min = 0;
        int max = x;
        while(min < max - 1) {
            int m = (min+max) / 2;
            if(x/m < m) {
                max = m;
            } else {
                min = m;
            }
        }
        return min;
    }
}
```
