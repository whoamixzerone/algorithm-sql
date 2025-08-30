# [PCCE 기출문제 6번 물 부족](https://school.programmers.co.kr/learn/courses/30/lessons/340202)

### 출처
#### 프로그래머스
[PCCE 기출문제 6번 물 부족](https://school.programmers.co.kr/learn/courses/30/lessons/340202)

#### 시간 복잡도
**change N(1 ≤ N ≤ 30)**  
$`O(N)`$

#### 문제 유형
구현

#### 문제 풀이

### c++ 풀이
```c++
#include <string>
#include <vector>

using namespace std;

int solution(int storage, int usage, vector<int> change) {
    int total_usage = 0;
    for(int i=0; i<change.size(); i++){
        usage += usage * change[i] / 100;
        total_usage += usage;
        if(total_usage > storage){
            return i;
        }
    }
    return -1;
}
```

### 다른 사람 풀이
```c++

```