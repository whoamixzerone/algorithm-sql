# [PCCE 기출문제 9번 지폐 접기](https://school.programmers.co.kr/learn/courses/30/lessons/340199)

### 출처
#### 프로그래머스
[PCCE 기출문제 9번 지폐 접기](https://school.programmers.co.kr/learn/courses/30/lessons/340199)

#### 시간 복잡도
**N(10 ≤ bill[0], bill[1] ≤ 2,000)**  
$`O(logN)`$

#### 문제 유형
구현  
그리디

#### 문제 풀이

### c++ 풀이
```c++
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

int solution(vector<int> wallet, vector<int> bill) {
    int answer = 0;
    while(min(wallet[0], wallet[1])<min(bill[0], bill[1])
         || max(wallet[0], wallet[1])<max(bill[0], bill[1])){
        if(bill[0]<bill[1]) bill[1]/=2;
        else bill[0]/=2;
        answer++;
    }
    return answer;
}
```

### 다른 사람 풀이
```c++
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

int solution(vector<int> wallet, vector<int> bill) {
    int answer = 0;
    sort(wallet.begin(), wallet.end());
    sort(bill.begin(), bill.end());
    while(wallet[0] < bill[0] || wallet[1] < bill[1])
    {
        bill[1] /= 2;
        if(bill[1] < bill[0])
        {
            int temp = bill[0];
            bill[0] = bill[1];
            bill[1] = temp;
        }
        answer++;
    }

    return answer;
}
```