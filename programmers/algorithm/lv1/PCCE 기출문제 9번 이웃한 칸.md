# [PCCE 기출문제 9번 이웃한 칸](https://school.programmers.co.kr/learn/courses/30/lessons/250125)

### 출처
#### 프로그래머스
[PCCE 기출문제 9번 이웃한 칸](https://school.programmers.co.kr/learn/courses/30/lessons/250125)

#### 시간 복잡도
$`O(1)`$

#### 문제 유형
구현

#### 문제 풀이

### c++ 풀이
```c++
#include <string>
#include <vector>

using namespace std;

int solution(vector<vector<string>> board, int h, int w) {
    int answer = 0;
    int dh[]={0, 1, -1, 0}, dw[]={1, 0, 0, -1};
    for(int i=0; i<4; ++i){
        int h_c=h+dh[i], w_c=w+dw[i];
        if(h_c<0||h_c>=board.size()||w_c<0||w_c>=board[0].size()) continue;
        if(board[h][w]==board[h_c][w_c]) answer++;
    }
    return answer;
}
```

### 다른 사람 풀이
```c++

```