# [PCCP 기출문제 1번 동영상 재생기](https://school.programmers.co.kr/learn/courses/30/lessons/340213)

### 출처
#### 프로그래머스
[PCCP 기출문제 1번 동영상 재생기](https://school.programmers.co.kr/learn/courses/30/lessons/340213)

#### 시간 복잡도
**schedules N(1 ≤ N ≤ 1,000)**  
$`O(N)`$

#### 문제 유형
구현

#### 문제 풀이

### c++ 풀이
```c++
#include <string>
#include <vector>
#include <iostream>
using namespace std;

string solution(string video_len, string pos, string op_start, string op_end, vector<string> commands) {
    string answer = "";
    int video_end=stoi(video_len.substr(0, 2))*60+stoi(video_len.substr(3, 2));
    int pos_time=stoi(pos.substr(0, 2))*60+stoi(pos.substr(3, 2));
    int ops_time=stoi(op_start.substr(0, 2))*60+stoi(op_start.substr(3, 2));
    int ope_time=stoi(op_end.substr(0, 2))*60+stoi(op_end.substr(3, 2));
    for(string c : commands){
        if(ops_time<=pos_time&&pos_time<=ope_time) pos_time=ope_time;
        if(c=="prev"){
            pos_time=pos_time-10<0?0:pos_time-10;
        } else if(c=="next"){
            pos_time=pos_time+10<=video_end?pos_time+10:video_end;
        }        
    }
    if(ops_time<=pos_time&&pos_time<=ope_time) pos_time=ope_time;
    string m=to_string(pos_time/60), s=to_string(pos_time%60);
    answer=(m.length()==1?"0"+m:m) + ":" + (s.length()==1?"0"+s:s);
    return answer;
}
```

### 다른 사람 풀이
```c++
#include <string>
#include <vector>
#include <iostream>

using namespace std;

int time(string str){    return (stoi(str)*60)+((str[3]-'0')*10)+str[4]-'0';}

string solution(string video_len, string pos, string op_start, string op_end, vector<string> commands) {
    string answer = "";
    int vl,p,ops,ope;
    vl=time(video_len);
    p=time(pos);
    ops=time(op_start);
    ope=time(op_end);

    for(int i=0;i<commands.size();i++)
    {
        if(ops<=p&&p<=ope)
            p=ope;

        if(commands[i]=="prev")
        {
            p-=10;
            if(p<0)
                p=0;
        }
        else
        {
            p+=10;
            if(p>vl)
                p=vl;
        }
    }
    if(ops<=p&&p<=ope)
            p=ope;

    if(p<600)
        answer+='0';
    answer+=to_string(p/60);
    answer+=':';
    if(p%60<10)
        answer+='0';
    answer+=to_string(p%60);

    return answer;
}
```

```c++
#include <string>
#include <algorithm>
using namespace std;

string solution(string video_len, string pos, string op_start, string op_end, vector<string> commands) {
    auto T = [](const string& s)
    {
        return (s[0] - '0') * 600 + (s[1] - '0') * 60 + (s[3] - '0') * 10 + (s[4]-'0');
    };
    int v = T(video_len), p = T(pos), a = T(op_start), b = T(op_end);
    auto S = [&]()
    { 
        if(a <= p && p <= b) p = b; 
    }; 
    S();
    for(auto& x : commands)
    { 
        p = x[0]=='p' ? max(0, p - 10) : min(v, p + 10); 
        S(); 
    }
    char r[6]; 
    sprintf(r,"%02d:%02d", p / 60, p % 60);
    return r;
}
```