# [Remove Element](https://leetcode.com/explore/learn/card/fun-with-arrays/526/deleting-items-from-an-array/3247/)

### 출처 LeetCode
[Remove Element](https://leetcode.com/explore/learn/card/fun-with-arrays/526/deleting-items-from-an-array/3247/)

#### 시간 복잡도
**n(1 <= nums.length <= 100)**   
$`O(n)`$

#### 문제 유형
구현  
Array  
투 포인터(two pointers)

#### 문제 풀이
현재 탐색하고 있는 요소는 왼쪽 포인터(`i`), 현재 배열의 유효한 끝 오른쪽 포인터(`n`)로  
`nums[i]==val`인 경우, `nums[i]`를 `nums[n-1`과 바꾸고 `n`을 감소하고 `val`이 아닌 경우엔 `i`를 증가시키면서 반복한다.

### c++ 풀이
```c++
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int i=0, n=nums.size();
        while (i<n) {
            if (nums[i]==val) {
                nums[i]=nums[n-1];
                --n;
            } else ++i;
        }
        return n;
    }
};
```

### 다른 사람 풀이
```c++
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int k = 0; // index to place the next valid element
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] != val) {
                nums[k] = nums[i];
                k++;
            }
        }
        return k;
    }
};
```