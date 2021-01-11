---
layout: post
title: "안드로이드 강의6 ListView"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2020-10-24 22:50:00 -0400
---

## ListView     
[홍드로이드님 안드로이드 강의 #6](https://youtu.be/snnqxAEf9rI)    


강의에서는 새로 empty프로젝트를 생성했으나  
나는 이전 SubActivity에 이어서 리스트뷰를 만들어보았다.     

<img src ="/assets/img/posts/Cap 2020-10-24 23-16-02-247.jpg">      

자바에서 자료구조는 처음인데,   
ArrayList가 List 인터페이스를 상속받은 클래스로     
크기가 가변적으로 변하는 선형리스트라고 한다.   
C++에서 list와 동일한 것 같다.      



### AndroidManifest.xml 파일 소스코드
```java
package com.example.study1;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.widget.ArrayAdapter;
import android.widget.ListView;
import android.widget.TextView;

import java.util.ArrayList;
import java.util.List;

public class SubActivity extends AppCompatActivity {

    private ListView list;
    private TextView tv_sub;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_sub);

        tv_sub = findViewById(R.id.tv_sub);

        list = (ListView)findViewById(R.id.list);
        List<String> data = new ArrayList<>();

        //list와 data를 담은, 중간다리 역할을 하는 어댑터 만듬
        ArrayAdapter<String> adapter = new ArrayAdapter<>(this, android.R.layout.simple_list_item_1, data);
        list.setAdapter(adapter); //리스트뷰에 어댑터 생성
        //adapter라는 이름으로 선언한 어댑터를 list에 세팅해줌

        //연결완료. 아이템 추가
        data.add("아이템1");
        data.add("아이템2");
        data.add("아이템3");
        adapter.notifyDataSetChanged(); //저장완료. 


        Intent intent = getIntent();
        String str = intent.getStringExtra("str");

        tv_sub.setText(str);


    }
}
```