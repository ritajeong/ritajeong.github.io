---
layout: post
title: "programmers lv1"
subtitle: "x만큼 간격이 있는 n개의 숫자"
categories: problem-solving
tags:  programmers algorithm vector
comments: true
date: 2020-07-31 21:05:00 -0400
---

구글링해서 참고한 코드임 ...  
순환을 위한 코드 저 부분이 너무 낯설어서 시간이 좀 걸렸다.  

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(string s, int n) {
    for(int i=0;i<s.size();i++){
        if(s[i] != ' '){
            char start = ('A'<=s[i] && s[i]<='Z')?'A':'a';
            s[i] = start + (s[i]+n-start)%26;
        }
    }
    return s;
}
```