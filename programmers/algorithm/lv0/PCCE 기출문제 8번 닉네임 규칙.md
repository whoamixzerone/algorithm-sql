# [PCCE 기출문제 8번 닉네임 규칙](https://school.programmers.co.kr/learn/courses/30/lessons/340200)

### 출처
#### 프로그래머스
[PCCE 기출문제 8번 닉네임 규칙](https://school.programmers.co.kr/learn/courses/30/lessons/340200)

#### 시간 복잡도
**nickname N(1 ≤ N ≤ 10)**  
$`O(N)`$

#### 문제 유형
구현

#### 문제 풀이

### c++ 풀이
```c++
#include <string>
#include <vector>

using namespace std;

string solution(string nickname) {
    string answer = "";
    for(int i=0; i<nickname.size(); i++){
        if(nickname[i] == 'l'){
            answer += "I";
        }
        else if(nickname[i] == 'w'){
            answer += "vv";
        }
        else if(nickname[i] == 'W'){
            answer += "VV";
        }
        else if(nickname[i] == 'O'){
            answer += "0";
        }
        else{
            answer += nickname[i];
        }
    }
    while(answer.size() < 4){
        answer += "o";
    }
    if(answer.size() > 8){
        answer = answer.substr(0,8);
    }
    return answer;
}
```

### 다른 사람 풀이
```c++

```