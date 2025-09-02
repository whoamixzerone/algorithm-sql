# [PCCE 기출문제 10번 공원](https://school.programmers.co.kr/learn/courses/30/lessons/340198)

### 출처
#### 프로그래머스
[PCCE 기출문제 10번 공원](https://school.programmers.co.kr/learn/courses/30/lessons/340198)

#### 시간 복잡도
**N, M(1 ≤ park, park[i] ≤ 50)**  
$`O(N * M)`$

#### 문제 유형
구현  
다이나믹 프로그래밍(DP)

#### 문제 풀이
DP를 이용해서 정사각형 최하단 오른쪽 지점의 값을 구할 수 있다.  
위쪽 값과 왼쪽 위 대각선 값, 왼쪽 값 중에 최소값에 1을 더한 값이 최하단 오른쪽 지점 값이 정사각형의 최대 변의 길이가 된다.

### c++ 풀이
```c++
#include <string>
#include <vector>
#include <cstring>
#include <algorithm>
using namespace std;

int solution(vector<int> mats, vector<vector<string>> park) {
    int answer = -1, mx=0, n=park.size(), m=park[0].size();
    int dp[n][m];
    memset(dp, 0, sizeof(dp));
    for(int i=0; i<n; ++i){
        for(int j=0; j<m; ++j){
            if(park[i][j]=="-1"){
                if(i==0||j==0) dp[i][j]=1;
                else dp[i][j]=min({dp[i-1][j], dp[i][j-1], dp[i-1][j-1]})+1;
                mx=max(mx, dp[i][j]);
            }
        }
    }
    sort(mats.rbegin(), mats.rend());
    for(int m : mats){
        if(m<=mx){
            answer=m;
            break;
        }
    }
    return answer;
}
```

### 다른 사람 풀이
```c++

```