# Friends Pairing Problem

Given N friends, each one can remain single or can be paired up with some other friend. Each friend can be paired only once. Find out the total number of ways in which friends can remain single or can be paired up.
Note: Since answer can be very large, return your answer mod 10^9+7.

```input
Input:N = 3
Output: 4
Explanation:
{1}, {2}, {3} : All single
{1}, {2,3} : 2 and 3 paired but 1 is single.
{1,2}, {3} : 1 and 2 are paired but 3 is single.
{1,3}, {2} : 1 and 3 are paired but 2 is single.
Note that {1,2} and {2,1} are considered same.
```

```java
class Solution
{
    static int mod=1000000007;
    public long  solution(int n,long[] dp){
        if(n==1){
            return 1;
        }
        if(n==2){
            return 2;
        }
        if(dp[n]!=0){
            return dp[n];
        }
        long val=(solution(n-1,dp)+(solution(n-2,dp)*(n-1))%mod)%mod;
        dp[n]=val;
        return val;
    }
    public long countFriendsPairings(int n)
    {
        return (long)solution(n,new long [n+1]);
    }
}
```
