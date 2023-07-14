# [K번째수](https://school.programmers.co.kr/learn/courses/30/lessons/42748)

### 출처 - 프로그래머스
[K번째수](https://school.programmers.co.kr/learn/courses/30/lessons/42748)

#### 문제 유형
정렬

### c++ 풀이
```c++
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

#define pb push_back
#define all(c) (c).begin(), (c).end()
#define EACH(x, a) for(auto& x: a)
vector<int> solution(vector<int> array, vector<vector<int>> commands) {
    vector<int> answer, temp;
    EACH(c, commands) {
        temp.assign(array.begin()+c[0]-1, array.begin()+c[1]);
        sort(all(temp));
        answer.pb(temp[c[2]-1]);
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

vector<int> solution(vector<int> array, vector<vector<int>> commands) {
    vector<int> answer;
    vector<int> temp;

    for(int i = 0; i < commands.size(); i++) {
        temp = array;
        sort(temp.begin() + commands[i][0] - 1, temp.begin() + commands[i][1]);
        answer.push_back(temp[commands[i][0] + commands[i][2]-2]);
    }

    return answer;
}
```