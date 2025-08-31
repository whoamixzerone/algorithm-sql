# [PCCE 기출문제 5번 산책](https://school.programmers.co.kr/learn/courses/30/lessons/250129)

### 출처
#### 프로그래머스
[PCCE 기출문제 5번 산책](https://school.programmers.co.kr/learn/courses/30/lessons/250129)

#### 시간 복잡도
**route N(1 ≤ N ≤ 20)**  
$`O(N)`$

#### 문제 유형
구현

#### 문제 풀이

### c++ 풀이
```c++
#include <string>
#include <vector>

using namespace std;

vector<int> solution(string route) {
    int east = 0;
    int north = 0;
    vector<int> answer(2);
    for(int i=0; i<route.length(); i++){
        switch(route[i]){
            case 'N':
                north++;
                break;
            case 'S':
                north--;
                break;
            case 'E':
                east++;
                break;
            case 'W':
                east--;
                break;
        }
    }
    answer[0] = east;
    answer[1] = north;
    return answer;
}
```

### 다른 사람 풀이
```c++

```