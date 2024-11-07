# Subset Sum Problem

Given an array of positive integers, arr[] and a value sum, determine if there is a subset of the given set with sum equal to given sum.

```
Input: arr[] = [3, 34, 4, 12, 5, 2], sum = 9
Output: true
Explanation: Here there exists a subset with sum = 9, 4+3+2 = 9.
```

```java
class Solution {

    static Boolean isSubsetSum(int arr[], int sum) {
        boolean[][] dp=new boolean[arr.length+1][sum+1];
        for(int i=0;i<dp.length;i++){
            for(int j=0;j<dp[0].length;j++){
                if(i==0 && j==0){
                    dp[i][j]=true;
                }else if(i==0){
                    dp[i][j]=false;
                }else if(j==0){
                    dp[i][j]=true;
                }else{
                    dp[i][j]=dp[i-1][j];
                    if(j>=arr[i-1]){
                        dp[i][j] |=dp[i-1][j-arr[i-1]];
                    }
                }
            }
        }
        return dp[dp.length-1][dp[0].length-1];
    }
}
```
