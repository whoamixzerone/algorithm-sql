# [PCCE 기출문제 10번 데이터 분석](https://school.programmers.co.kr/learn/courses/30/lessons/250121)

### 출처
#### 프로그래머스
[PCCE 기출문제 10번 데이터 분석](https://school.programmers.co.kr/learn/courses/30/lessons/250121)

#### 시간 복잡도
$`O(NlogN)`$

#### 문제 유형
구현  
정렬

#### 문제 풀이

### c++ 풀이
```c++
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

vector<vector<int>> solution(vector<vector<int>> data, string ext, int val_ext, string sort_by) {
    vector<vector<int>> answer;    
    int idx=0;
    if(sort_by == "code") idx=0;
    else if(sort_by == "date") idx=1;
    else if(sort_by == "maximum") idx=2;
    else idx=3;
    sort(data.begin(), data.end(), [idx](const vector<int>& a, const vector<int>& b) {
        return a[idx]<b[idx];
    });
    for(auto d : data){
        if(ext=="code"){
            if(d[0]<val_ext) answer.push_back(d);            
        } else if(ext=="date"){
            if(d[1]<val_ext) answer.push_back(d);
        } else if(ext=="maximum"){
            if(d[2]<val_ext) answer.push_back(d);
        } else {
            if(d[3]<val_ext) answer.push_back(d);
        }
    }    

    return answer;
}
```

### 다른 사람 풀이
```c++
#include <string>
#include <vector>
#include <algorithm>
#include <unordered_map>

using namespace std;

vector<vector<int>> solution(vector<vector<int>> data, string ext, int val_ext, string sort_by) {
    vector<vector<int>> answer;
    unordered_map<string, int> name_to_idx;
    name_to_idx["code"] = 0;
    name_to_idx["date"] = 1;
    name_to_idx["maximum"] = 2;
    name_to_idx["remain"] = 3;

    auto it = remove_if(data.begin(), data.end(), [idx=name_to_idx[ext], val_ext](const auto& row) {
        return !(row[idx] < val_ext);
    });
    data.erase(it, data.end());

    sort(data.begin(), data.end(), [idx=name_to_idx[sort_by]](const auto& row1, const auto& row2) {
        return row1[idx] < row2[idx];
    });
    return data;
}
```

```c++
#include <string>
#include <vector>
#include <unordered_map>
#include <algorithm>

using namespace std;

vector<vector<int>> solution(vector<vector<int>> data, string ext, int val_ext, string sort_by) {
    vector<vector<int>> answer;
    unordered_map<string, int> mapping{{"code",0},{"date",1},{"maximum",2},{"remain",3}};

    for (vector<int>& datum:data){
        if (datum[mapping[ext]] < val_ext)
            answer.push_back(datum);
    }

    sort(answer.begin(), answer.end(), [&](vector<int>& a, vector<int>& b){return a[mapping[sort_by]] < b[mapping[sort_by]];});

    return answer;
}
```