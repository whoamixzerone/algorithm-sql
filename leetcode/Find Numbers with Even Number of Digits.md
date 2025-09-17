# [Find Numbers with Even Number of Digits](https://leetcode.com/explore/learn/card/fun-with-arrays/521/introduction/3237/)

### 출처 LeetCode
[Find Numbers with Even Number of Digits](https://leetcode.com/explore/learn/card/fun-with-arrays/521/introduction/3237/)

#### 시간 복잡도
**n(1 <= nums.length <= 500)**  
$`O(n)`$

#### 문제 유형
구현  
Array

#### 문제 풀이

### c++ 풀이
```c++
class Solution {
public:
    int findNumbers(vector<int>& nums) {
        int answer=0;
        for(int n : nums) {
            int digit=0;
            while(n) {
                n/=10;
                digit++;
            }
            if(digit%2==0) answer++;
        }
        return answer;
    }
};
```

### 다른 사람 풀이
```c++

```