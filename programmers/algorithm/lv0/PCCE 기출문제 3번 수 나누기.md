# [PCCE 기출문제 3번 수 나누기](https://school.programmers.co.kr/learn/courses/30/lessons/340205)

### 출처
#### 프로그래머스
[PCCE 기출문제 3번 수 나누기](https://school.programmers.co.kr/learn/courses/30/lessons/340205)

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
    int number;
    cin >> number;
    
    int answer = 0;
    
    while(number!=0) {
        answer += number % 100;
        number /= 100;
    }
    cout << answer << endl;
    return 0;
}
```

### 다른 사람 풀이
```c++

```