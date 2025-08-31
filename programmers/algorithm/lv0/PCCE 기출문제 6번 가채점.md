# [PCCE 기출문제 6번 가채점](https://school.programmers.co.kr/learn/courses/30/lessons/250128)

### 출처
#### 프로그래머스
[PCCE 기출문제 6번 가채점](https://school.programmers.co.kr/learn/courses/30/lessons/250128)

#### 시간 복잡도
**numbers N(1 ≤ N ≤ 10)**  
$`O(N)`$

#### 문제 유형
구현

#### 문제 풀이

### c++ 풀이
```c++
#include <string>
#include <vector>

using namespace std;

vector<string> solution(vector<int> numbers, vector<int> our_score, vector<int> score_list) {
    int num_student = numbers.size();
    vector<string> answer(num_student);
    
    for (int i = 0; i < num_student; i++) {
        if (our_score[i] == score_list[numbers[i]-1]) {
            answer[i] = "Same";
        }
        else {
            answer[i] = "Different";
        }
    }
    
    return answer;
}
```

### 다른 사람 풀이
```c++

```