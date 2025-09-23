# [Remove Duplicates from Sorted Array](https://leetcode.com/explore/learn/card/fun-with-arrays/526/deleting-items-from-an-array/3248/)

### 출처 LeetCode
[Remove Duplicates from Sorted Array](https://leetcode.com/explore/learn/card/fun-with-arrays/526/deleting-items-from-an-array/3248/)

#### 시간 복잡도
**n(1 <= nums.length <= 3 * 10^4)**   
$`O(n)`$

#### 문제 유형
구현  
Array  
투 포인터(two pointers)

#### 문제 풀이

### c++ 풀이
```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        return unique(nums.begin(), nums.end())-nums.begin();
    }
};
```

### 다른 사람 풀이
```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int i = 0;
        int n = nums.size();
        for(int j = 1; j < n; j++){
            if(nums[j] != nums[i]){
                nums[i+1] = nums[j];
                i++;
            }
        }
        return i + 1;
    }
};
```