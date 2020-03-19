实现 strStr() 函数（indexOf()函数）。
给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回-1。  
```java
//KMP
class Solution {
  public int strStr(String haystack, String needle) {
    if(haystack.length() == 0 || haystack == null)  return -1;
    int m = haystack.length();
    int n = needle.length();
    for(int i=0;i<m-n+1;i++) {
      int j = 0;
      for(j=0;j<n;j++) {
        if(haystack.charAt(i+j) !== needle.charAt(j)) {
          break;
        }
      }
      if(j == n) {
        return i;
      }
    }
    return -1;
  }
}
```
