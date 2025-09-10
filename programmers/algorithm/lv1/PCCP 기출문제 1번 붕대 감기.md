# [PCCP 기출문제 1번 붕대 감기](https://school.programmers.co.kr/learn/courses/30/lessons/250137)

### 출처
#### 프로그래머스
[PCCP 기출문제 1번 붕대 감기](https://school.programmers.co.kr/learn/courses/30/lessons/250137)

#### 시간 복잡도
**1 ≤ 공격시간 ≤ 1,000**  
$`O(1)`$

#### 문제 유형
구현  
정렬

#### 문제 풀이

### c++ 풀이
```c++
#include <string>
#include <vector>
#include <iostream>
using namespace std;

int solution(vector<int> bandage, int health, vector<vector<int>> attacks) {
    int answer=health;
    int end_time=attacks.back()[0];
    int cnt=0, time=0;
    for(int i=1; i<=end_time; ++i){
        if(i==attacks[time][0]){
            answer-=attacks[time][1];
            if(answer<=0) return -1;
            ++time;
            cnt=0;
        } else {
            answer+=bandage[1];
            ++cnt;
            if(cnt==bandage[0]){
                answer+=bandage[2];
                cnt=0;
            }
            if(health<answer) answer=health;
        }
    }
    return answer;
}
```

### 다른 사람 풀이
```c++
#include <string>
#include <vector>

using namespace std;

int solution(vector<int> bandage, int health, vector<vector<int>> attacks) {
    int maxhealth = health, time = 0;
    for(int i=0;i<attacks.size();i++){
        int dTime = attacks[i][0];
        int damage=attacks[i][1];
        int diff = dTime - time-1;
        health += diff*bandage[1] +diff/bandage[0] * bandage[2];
        if(health > maxhealth) health = maxhealth;
        health-=damage;
        time = dTime;
        if(health<=0) break;
    }
    return health<=0 ? -1:health;
}
```