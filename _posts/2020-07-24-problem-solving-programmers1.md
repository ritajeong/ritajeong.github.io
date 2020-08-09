---
layout: post
title: "programmers 소수찾기"
subtitle: ""
categories: problem-solving
tags:  programmers algorithm bruteforce
comments: true
date: 2020-07-24 12:56:00 -0400
---

```cpp
#include <iostream>
using namespace std;
int arr[100];
bool Prime(int x) {
	if (x == 1)
		return false;
	else if (x == 2)
		return true;
	else {
		for (int i = 2; i < x; i++) {
			if (x % i == 0)
				return false;
		}
	}
	return true;
}
int main() {
	int n;
	cin >> n;
	int cnt = 0;
	for (int i = 0; i < n; i++) {
		cin >> arr[i];
		if (Prime(arr[i]))
			cnt++;
	}
	cout << cnt;
}
```

정확성  테스트
테스트 1 〉	통과 (0.00ms, 3.86MB)
테스트 2 〉	통과 (0.01ms, 3.84MB)
테스트 3 〉	통과 (0.05ms, 3.84MB)
테스트 4 〉	통과 (0.19ms, 3.79MB)
테스트 5 〉	통과 (0.10ms, 3.74MB)
테스트 6 〉	통과 (10.09ms, 3.81MB)
테스트 7 〉	통과 (1.02ms, 3.77MB)
테스트 8 〉	통과 (5.04ms, 3.84MB)
테스트 9 〉	통과 (13.12ms, 3.89MB)
테스트 10 〉	통과 (7664.82ms, 3.82MB)
테스트 11 〉	실패 (시간 초과)
테스트 12 〉	통과 (9456.45ms, 3.76MB)
효율성  테스트
테스트 1 〉	실패 (시간 초과)
테스트 2 〉	실패 (시간 초과)
테스트 3 〉	실패 (시간 초과)
테스트 4 〉	실패 (시간 초과)
채점 결과
정확성: 68.8
효율성: 0.0
합계: 68.8 / 100.0

함수호출이 너무 잦은가?
재수정해보기.