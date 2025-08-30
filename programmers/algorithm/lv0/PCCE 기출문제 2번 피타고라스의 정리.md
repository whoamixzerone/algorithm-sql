# [PCCE 기출문제 2번 피타고라스의 정리](https://school.programmers.co.kr/learn/courses/30/lessons/250132)

### 출처
#### 프로그래머스
[PCCE 기출문제 2번 피타고라스의 정리](https://school.programmers.co.kr/learn/courses/30/lessons/250132)

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
    int a;
    int c;
    cin >> a >> c;
    
    int b_square = c*c - a*a;
    cout << b_square << endl;
    return 0;
}
```

### 다른 사람 풀이
```c++

```