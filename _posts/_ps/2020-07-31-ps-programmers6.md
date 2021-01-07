---
layout: post
title: "programmers lv1 콜라츠 추측"
subtitle: "콜라츠 추측"
categories: ps
tags: ps
comments: true
date: 2020-07-31 20:16:00 -0400
---

```cpp
#include <string>
#include <vector>
using namespace std;
int solution(int num) {
    int answer = 0;
    long long n= num; //범위 초과될 수 있어서!!!
    while(n!=1){
        if(answer==500){
            return -1;
        }
        if(n&1){
            n= n*3 +1;
        }
        else{
            n/=2;
        }
        answer++;
    }
    return answer;
}
```

3을 곱하는 과정이 있는데,  
여기서 범위가 초과할 거란 생각은 미처 못했다.  
자료형때문에 틀리는 줄 모르고 한 10분은 멍때린 것 같음 ㅠ  

+ 추가로 n&1 표현 구글링해서 득템함 ㅎㅎ