# 알고리즘 문제와 SQL 문제 기록

**bits/stdc++.h** 👉 [gcc github](https://github.com/whoamixzerone/gcc)  
**gcc > libstdc++-v3 > include > precompiled > stdc++.h** 위치


> c++ 선언문들은 "tmwilliamlin168"님의 코드를 참조했습니다.  
[github](https://github.com/tmwilliamlin168)  
[youtube](https://www.youtube.com/@tmwilliamlin168)

```c++
#include <bits/stdc++.h>
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

const int d4i[4]={-1, 0, 1, 0}, d4j[4]={0, 1, 0, -1};
const int d8i[8]={-1, -1, 0, 1, 1, 1, 0, -1}, d8j[8]={0, 1, 1, 1, 0, -1, -1, -1};
```