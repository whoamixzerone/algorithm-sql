# [Max Consecutive Ones](https://leetcode.com/explore/learn/card/fun-with-arrays/521/introduction/3238/)

### 출처 LeetCode
[Max Consecutive Ones](https://leetcode.com/explore/learn/card/fun-with-arrays/521/introduction/3238/)

#### 시간 복잡도
**n(1 <= nums.length <= 10^5)**  
$`O(n)`$

#### 문제 유형
구현  
Array

#### 문제 풀이

### c++ 풀이
```c++
class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& nums) {
        int cnt=0, answer=0;
        for(int n : nums) {            
            if(!n) {                
                cnt=0;
                continue;
            }
            cnt++;
            answer=max(answer, cnt);
        }
        return answer;
    }
};
```

### 다른 사람 풀이
```c++

```