# [n의 배수 고르기](https://school.programmers.co.kr/learn/courses/30/lessons/120905)

### 출처
#### 프로그래머스
[n의 배수 고르기](https://school.programmers.co.kr/learn/courses/30/lessons/120905)

#### 문제 내용
```numlist```에서 ```n```의 배수가 아닌 수들을 제거한 배열을 반환

#### 문제 풀이
구현 문제  
배열을 돌면서 배수인 수들만 골라낸다

### c++ 풀이
```c++
#include <string>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;

#define ll long long
#define ld long double
#define ar array

#define vt vector
#define pb push_back
#define sz(x) (int)(x).size()
#define all(c) (c).begin(), (c).end()

#define F_OR(i, b, e, s) for(int i=(b); (s)>0?i<(e):i>(e); i+=(s))
#define F_OR1(e) F_OR(i, 0, e, 1)
#define F_OR2(i, e) F_OR(i, 0, e, 1)
#define F_OR3(i, b, e) F_OR(i, b, e, 1)
#define F_OR4(i, b, e, s) F_OR(i, b, e, s)
#define GET5(a, b, c, d, e, ...) e
#define F_ORC(...) GET5(__VA_ARGS__, F_OR4, F_OR3, F_OR2, F_OR1)
#define FOR(...) F_ORC(__VA_ARGS__)(__VA_ARGS__)
#define EACH(x, a) for(auto& x: a)

template<class T> void read(T& x) {
	cin >> x;
}
template<class H, class... T> void read(H& h, T&... t) {
	read(h);
	read(t...);
}

string to_string(char c) {
	return string(1, c);
}
string to_string(bool b) {
	return b?"true":"false";
}
string to_string(const char* s) {
	return string(s);
}
string to_string(string s) {
	return s;
}

template<class T> void write(T x) {
	cout << to_string(x);
}
template<class H, class... T> void write(const H& h, const T&... t) {
	write(h);
	write(t...);
}

void print() {
	write("\n");
}
template<class H, class... T> void print(const H& h, const T&... t) {
	write(h);
	if(sizeof...(t))
		write(' ');
	print(t...);
}

vector<int> solution(int n, vector<int> numlist) {
    vector<int> answer;
    EACH(i, numlist)
        if(!(i%n))
            answer.pb(i);
    return answer;
}
```