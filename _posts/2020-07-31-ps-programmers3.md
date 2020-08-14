---
layout: post
title: "programmers lv1 이상한 문자 제거하기"
subtitle: "이상한 문자 제거하기"
categories: ps
tags: ps
comments: true
date: 2020-07-31 18:09:00 -0400
---

공백을 기준으로 입력받은 s를 토큰으로 나누어야하나 잠깐동안 고민했음.  
그러나 생각을 바꿔서, i를 기준으로 작동하는 포문 1개에서 j변수를 같이 사용하기로 했다.  
아스키코드 기준으로 [65,91]이 대문자, [97,123]이 소문자다.  
알파벳 개수는 26개지만 대문자와 소문자 사이의 간격은 32라서, 소문자에서 32를 빼면 대문자가 되고 대문자일 때 32를 더하면 소문자가 되는 것을 이용했다.
```cpp
#include <string>
#include <vector>

using namespace std;

string solution(string s) {
    int i,j=0;
    for(i=0;i<s.size();i++){
        j++;
        if(j%2){//65 97
            if(s[i]>=97 && s[i]<=123)//소문자면
                s[i]-=32;//대문자로
        }
        else{
            if(s[i] < 97&&s[i]>=65) //대문자면
                s[i]+=32;//소문자로
        }
        if(s[i] == ' ')
            j=0;
    }
    return s;
}
```

