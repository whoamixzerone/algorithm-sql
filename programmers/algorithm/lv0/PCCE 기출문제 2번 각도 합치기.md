# [PCCE 기출문제 2번 각도 합치기](https://school.programmers.co.kr/learn/courses/30/lessons/340206)

### 출처
#### 프로그래머스
[PCCE 기출문제 2번 각도 합치기](https://school.programmers.co.kr/learn/courses/30/lessons/340206)

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
    int angle1;
    int angle2;
    cin >> angle1 >> angle2;
    
    int sum_angle = angle1 + angle2;
    cout << (sum_angle%360) << endl;
    return 0;
}
```

### 다른 사람 풀이
```c++

```