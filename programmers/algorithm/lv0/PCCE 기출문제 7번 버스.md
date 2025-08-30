# [PCCE 기출문제 7번 버스](https://school.programmers.co.kr/learn/courses/30/lessons/340201)

### 출처
#### 프로그래머스
[PCCE 기출문제 7번 버스](https://school.programmers.co.kr/learn/courses/30/lessons/340201)

#### 시간 복잡도
**passengers N(1 ≤ N ≤ 10)**  
$`O(N)`$

#### 문제 유형
구현

#### 문제 풀이

### c++ 풀이
```c++
#include <string>
#include <vector>

using namespace std;

int func1(int num){
    if(0 > num){
        return 0;
    }
    else{
        return num;
    }
}

int func2(int num){
    if(num > 0){
        return 0;
    }
    else{
        return num;
    }
}

int func3(vector<string> station){
    int num = 0;
    for(int i=0; i<station.size(); i++){
        if(station[i] == "Off"){
            num += 1;
        }
    }
    return num;
}

int func4(vector<string> station){
    int num = 0;
    for(int i=0; i<station.size(); i++){
        if(station[i] == "On"){
            num += 1;
        }
    }
    return num;
}

int solution(int seat, vector<vector<string>> passengers) {
    int num_passenger = 0;
    for(int i=0; i<passengers.size(); i++){
        num_passenger += func4(passengers[i]);
        num_passenger -= func3(passengers[i]);
    }
    int answer = func1(seat-num_passenger);
    return answer;
}
```

### 다른 사람 풀이
```c++

```