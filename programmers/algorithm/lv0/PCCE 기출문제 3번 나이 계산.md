# [PCCE 기출문제 3번 나이 계산](https://school.programmers.co.kr/learn/courses/30/lessons/250131)

### 출처
#### 프로그래머스
[PCCE 기출문제 3번 나이 계산](https://school.programmers.co.kr/learn/courses/30/lessons/250131)

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
    int year, answer;
    string age_type;
    cin >> year >> age_type;

    if (age_type == "Korea") {
        answer = 2030-year+1;
    }
    else if (age_type == "Year") {
        answer = 2030-year;
    }

    cout << answer << endl;
    return 0;
}
```

### 다른 사람 풀이
```c++

```