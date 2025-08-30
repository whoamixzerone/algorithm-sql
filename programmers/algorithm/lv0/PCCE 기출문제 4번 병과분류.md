# [PCCE 기출문제 4번 병과분류](https://school.programmers.co.kr/learn/courses/30/lessons/340204)

### 출처
#### 프로그래머스
[PCCE 기출문제 4번 병과분류](https://school.programmers.co.kr/learn/courses/30/lessons/340204)

#### 시간 복잡도
$`O(1)`$

#### 문제 유형
구현

#### 문제 풀이

### c++ 풀이
```c++
#include <iostream>

using namespace std;

int main(void) {
    string code;
    cin >> code;
    string last_four_words = code.substr(code.size()-4, 4);
    if(last_four_words == "_eye"){
        cout << "Ophthalmologyc";
    }
    else if(last_four_words == "head"){
        cout << "Neurosurgery";
    }
    else if(last_four_words == "infl"){
        cout << "Orthopedics";
    }
    else if(last_four_words == "skin"){
        cout << "Dermatology";
    }
    else {
        cout << "direct recommendation";
    }
    return 0;
}
```

### 다른 사람 풀이
```c++

```