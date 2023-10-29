# 50. Pow(x, n)
---

# Intuition
Dynamic Programming

# Approach
keep breaking the power to be found evenly
- if n is even : break ```n``` into ```n/2``` and ```n/2```
- if n is odd : break ```n``` into ```n/2``` and ```n/2 + 1```

now take the tree form n to 0, and return the result on the way back from 0 to n.

# Complexity
- Time complexity: O(n)

- Space complexity: O(n)

# Code
```
class Solution {
    map<int,double> memo;
    double calculator(double x, int n) {
        if(n == 1)
            return x;
        if(memo.find(n) != memo.end())
            return memo[n];
        if(fmod(n,2) == 0) {
            double res = calculator(x,n/2) * calculator(x,n/2);
            memo[n] = res;
            return res;
        }
        else {
            double res = calculator(x,(n/2)+1) * calculator(x,n/2);
            memo[n] = res;
            return res;
        }
        return 1;
    }
public:
    double myPow(double x, int n) {
        if(x == 0)
            return 0;
        else if(x == 1)
            return 1;
        else if(n == 0)
            return 1;
        else if( n == -2147483648)
            return 1/x * calculator(1/x, -(n+1));
        if(n > 0)
            return calculator(x,n);
        else if(n < 0)
            return calculator(1/x,-n);

        return 1;
    }
};
```