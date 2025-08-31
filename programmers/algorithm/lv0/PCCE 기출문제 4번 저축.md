# [PCCE 기출문제 4번 저축](https://school.programmers.co.kr/learn/courses/30/lessons/250130)

### 출처
#### 프로그래머스
[PCCE 기출문제 4번 저축](https://school.programmers.co.kr/learn/courses/30/lessons/250130)

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
    int start;
    int before;
    int after;
    cin >> start >> before >> after;

    int money = start;
    int month = 1;

    while (money < 70) {
        money += before;
        month++;
    }
    while (money < 100) {
        money += after;
        month++;
    }
    cout << month << endl;
    return 0;
}
```

### 다른 사람 풀이
```c++

```