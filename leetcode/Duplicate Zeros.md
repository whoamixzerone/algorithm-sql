# [Duplicate Zeros](https://leetcode.com/explore/learn/card/fun-with-arrays/525/inserting-items-into-an-array/3245/)

### 출처 LeetCode
[Duplicate Zeros](https://leetcode.com/explore/learn/card/fun-with-arrays/525/inserting-items-into-an-array/3245/)

#### 시간 복잡도
**n(1 <= arr.length <= 10^4)**  
$`O(n)`$

#### 문제 유형
구현  
Array  
투 포인터(two pointers)

#### 문제 풀이
오른쪽으로 시프트 해야 하는데 배열 크기는 고정이기 때문에 뒤에서부터 덮어써야 한다.  
투 포인터로 하나는 원래 위치(`i`), 하나는 실제로 값을 써야 할 위치(`j=i+zeros`)로 구분한다.  

0의 갯수를 구한다. 0의 갯수는 총 오른쪽 시프트 해야 할 갯수를 뜻한다.  
단, `i+zeros`는 배열의 범위를 넘을 수 있기 때문에(Out of bounds) 조건으로 확인한다.  
`arr[i]`가 0이고 배열 범위 안이라면 복제된 0을 복사하고, 그다음 자리(`j-1`)에 또 0을 써야 하기 때문에 `--zeros`, `--j`를 해준다.  
배열 범위 안이라면 `arr[j]=arr[i]`로 그냥 복사한다.

### c++ 풀이
```c++
class Solution {
public:
    void duplicateZeros(vector<int>& arr) {
        int n = arr.size();
        int zeros = 0;
        for(int a : arr) {
            if(!a) ++zeros;
        }
        for(int i=n-1; i>=0; --i) {
            int j=i+zeros;
            if(!arr[i]) {
                if(j<n) arr[j]=0;
                --zeros;
                --j;
            }
            if(j<n) arr[j]=arr[i];
        }
    }
};
```

### 다른 사람 풀이
```c++

```