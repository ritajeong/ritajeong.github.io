---
layout: post
title: "programmers lv1 제일 작은 수 제거하기"
subtitle: "제일 작은 수 제거하기"
categories: ps
tags: ps
comments: true
date: 2020-07-31 18:09:00 -0400
---

벡터를 사용해서 간단하게 풀 수 있는 문제였다.  
굳이 반환하는 벡터 vector<int> answer를 할당하지 않고 arr를 재활용했다.  
처음에는 최소값을 포문에서 일일이 찾아서 벡터 answer에 복사하는 코드를 써봤는데 시간초과가 났었다.  
아래가 최종 작성한 코드. STL vector에서 min_element와 erase를 적절히 사용했다.  
```cpp
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

vector<int> solution(vector<int> arr) {
    if(arr.size()==1)
        arr[0] = -1;
    else{
        arr.erase(min_element(arr.begin(), arr.end()));
    }
    return arr;
}
```

