
# Fraction to recurring decimal

[![Problem Link](https://leetcode.com/problems/fraction-to-recurring-decimal/)](link)


### Sample Input
```
Input: numerator = 1, denominator = 2
```
### Sample Output
```
Output: "0.5"
```

### Solution
```cpp
class Solution {
public:
    string fractionToDecimal(int numerator, int denominator) {
        if(!numerator) return "0";
        string ans = "";
        if (numerator > 0 ^ denominator > 0) ans += '-';
        long num = labs(numerator), den = labs(denominator);
        long q = num / den;
        long r = num % den;
        ans += to_string(q);
        
        if(r == 0) return ans;
        
        ans += '.';
        unordered_map<long, int> mp;
        while(r != 0){
            if(mp.find(r) != mp.end()){
                int pos = mp[r];
                ans.insert(pos, "(");
                ans += ')';
                break;
            }
            else{
                mp[r] = ans.length();
                r *= 10;
                q = r / den;
                r = r % den;
                ans += to_string(q);
            }
        }
        return ans;
    }
};
```

### Accepted
[![image](link)](link)
