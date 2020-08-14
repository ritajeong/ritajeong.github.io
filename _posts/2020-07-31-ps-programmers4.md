---
layout: post
title: "programmers lv1 x만큼 간격이 있는 n개의 숫자"
subtitle: "x만큼 간격이 있는 n개의 숫자"
categories: ps
tags: ps
comments: true
date: 2020-07-31 18:48:00 -0400
---

```cpp
#include <string>
#include <vector>

using namespace std;

vector<long long> solution(int x, int n) {
    vector<long long> answer(n);
    int cnt = x;
    answer[0]=x;
    for(int i=1;i<n;i++){
        x+=cnt;
        answer[i] = x;
    }
    return answer;
}
```  
이렇게 제출했는데, 다른 사람의 풀이보기>를 확인하고 왔더니  
확실히 내 코드가 별로긴 하다..ㅎ..
```cpp
#include <string>
#include <vector>

using namespace std;

vector<long long> solution(int x, int n) {
    vector<long long> answer;
   for(int i=0;i<n;i++)
    answer.push_bask((i+1)*x);
    return answer;
}
```  

포문의 성질과 등비수열의 원리를 생각하면  
이렇게 간단하게도 짤 수 있는데,  
push_back의 성능이 좋지 않다는 말이 생각나서 벡터를 n개만큼 먼저 할당하고 싶었다...ㅎ  
그럼에도 불구하고 짧은 코드지만 비효율적인 것처럼 보인다.   
나처럼 인덱스를 연산을 활용한 다른 코드를 참고해보니,
```cpp
    vector<long long> answer(n, x);

    for (int i = 1; i < n; i++)
        answer[i] = answer[i - 1] + x;
```
이렇게 제출한 사람들도 있었다.  
제일 좋아보임!