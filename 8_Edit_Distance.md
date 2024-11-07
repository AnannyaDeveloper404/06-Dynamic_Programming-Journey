# Edit Distance

Given two strings s1 and s2. Return the minimum number of operations required to convert s1 to s2.
The possible operations are permitted:

Insert a character at any position of the string.
Remove any character from the string.
Replace any character from the string with any other character.

```
Input: s1 = "geek", s2 = "gesek"
Output: 1
Explanation: One operation is required, inserting 's' between two 'e'.
```

```java

class Solution {
    public int editDistance(String s1, String s2) {
        int n=s1.length(),m=s2.length();
        int[][] dp=new int[n+1][m+1];
        for(int i=dp.length-1;i>=0;i--){
            for(int j=dp[0].length-1;j>=0;j--){
               if(i==dp.length-1 && j==dp[0].length-1 ){
                   dp[i][j]=0;
               }else if(i==dp.length-1){
                   dp[i][j]=dp[i][j+1]+1;
               }else if(j==dp[0].length-1){
                   dp[i][j]=dp[i+1][j]+1;
               }else{
                   if(s1.charAt(i)!=s2.charAt(j)){
                       dp[i][j]=Math.min(dp[i+1][j],Math.min(dp[i][j+1],dp[i+1][j+1]))+1;
                   }else{
                       dp[i][j]=dp[i+1][j+1];
                   }
               }

            }
        }
        return dp[0][0];
    }
}
```
