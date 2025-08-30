# [PCCE 기출문제 5번 심폐소생술](https://school.programmers.co.kr/learn/courses/30/lessons/340203)

### 출처
#### 프로그래머스
# [PCCE 기출문제 5번 심폐소생술](https://school.programmers.co.kr/learn/courses/30/lessons/340203)

#### 시간 복잡도
$`O(5^2)`$

#### 문제 유형
구현

#### 문제 풀이

### c++ 풀이
```c++
#include <string>
#include <vector>

using namespace std;

vector<int> solution(vector<string> cpr) {
    vector<int> answer = {0, 0, 0, 0, 0};
    vector<string> basic_order = {"check", "call", "pressure", "respiration", "repeat"};

    for(int i=0; i<cpr.size(); i++){
        for(int j=0; j<basic_order.size(); j++){
            if(cpr[i] == basic_order[j]){
                answer[i] = j+1;
                break;
            }
        }
    }

    return answer;
}
```

### 다른 사람 풀이
```c++

```