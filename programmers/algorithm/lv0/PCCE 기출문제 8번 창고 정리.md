# [PCCE 기출문제 8번 창고 정리](https://school.programmers.co.kr/learn/courses/30/lessons/250126)

### 출처
#### 프로그래머스
[PCCE 기출문제 8번 창고 정리](https://school.programmers.co.kr/learn/courses/30/lessons/250126)

#### 시간 복잡도
**storage N(1 ≤ N ≤ 30)**  
$`O(N^2)`$

#### 문제 유형
구현

#### 문제 풀이

### c++ 풀이
```c++
#include <string>
#include <vector>

using namespace std;

string solution(vector<string> storage, vector<int> num) {
    int num_item = 0;
    vector<string> clean_storage(storage.size());
    vector<int> clean_num(num.size());
    
    for(int i=0; i<storage.size(); i++){
        int clean_idx = -1;
        for(int j=0; j<num_item; j++){
            if(storage[i] == clean_storage[j]){
                clean_idx = j;
                break;
            }
        }
        if(clean_idx == -1){
            clean_storage[num_item] = storage[i];
            clean_num[num_item] = num[i];
            num_item += 1;
        }
        else{
            clean_num[clean_idx] += num[i];
        }
    }
    
    int num_max = -1;
    string answer = "";
    for(int i=0; i<num_item; i++){
        if(clean_num[i] > num_max){
            num_max = clean_num[i];
            answer = clean_storage[i];
        }
    }
    return answer;
}
```

### 다른 사람 풀이
```c++

```