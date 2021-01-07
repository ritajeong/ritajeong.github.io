---
layout: post
title: "programmers lv1 하샤드 수"
subtitle: "하샤드 수"
categories: ps
tags: ps
comments: true
date: 2020-07-31 19:32:00 -0400
---

```cpp
#include <string>
#include <vector>

using namespace std;

bool solution(int x) {
    bool answer = true;
    string s = to_string(x);
    int sum=0;
    for(int i=0;i<s.size();i++ ){
        sum=sum+s[i]-48;
    }
    if(x% sum)
        answer = false;
    return answer;
}
```

다른 사람들의 풀이와 비교해보니,
보통 자릿수를 / 랑 %를 사용해서 풀었던데..  
나는 저 연산이 유난히 맘에 안 들어서??(매우 안 좋은 감정적이고 주관적인 변명)  
스트링을 쓰는 걸 선호한다.  
자릿수를 / %로 하는 걸 기본으로 잘 알고 잘 다룰 수 있는 상황에서 스트링을 하는 건 완벽하다고 생각하지만  
이런 식의 도피성 스트링 사용은(?)   
매우 부적절한 것 같다.....  
