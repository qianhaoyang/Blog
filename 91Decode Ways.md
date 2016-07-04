# <h1>91. Decode Ways

###### Solution: Use DP.
###### in this problem we have only 4 cases for each char:
###### 1:only can conbined with the pre char,dp[i] = dp[i-2]
###### 2:only can be self alone,dp[i] = dp[i-1]
###### 3:can be both 1 and 2,dp[i] = dp[i-2] + dp[i-1]
###### 4:both can not,return 0 
```
    int numDecodings(string s) {
        if(s[0] == '0') return 0;
        int* dp = new int[s.size()];
        dp[0] = 1;
        for(int i = 1;i < s.size();i++){
            int temp = (s[i-1]-'0')*10 + (s[i]-'0');
            
            /*for case 1*/
            if(temp == 10 || temp == 20){
                dp[i] =  i >=2 ? dp[i-2] : 1;
            }
            
            /*for case 4*/
            else if(temp % 10 == 0){
                return 0;
            }
            
            /*for case 3*/
            else if(temp <= 26 && temp>=10){
                dp[i] = i >=2 ? dp[i-2] + dp[i-1]:2;
            }
            
            /*for case 2*/
            else{
                dp[i] = i >=2 ? dp[i-1]:1;
            }
        }
        return dp[s.size()-1];
    }
```
