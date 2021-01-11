---
layout: post
title: "안드로이드 강의3 Intent 화면전환"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2020-10-24 05:23:00 -0400
---

## Intent 화면전환  
[홍드로이드님 안드로이드 강의 #3](https://youtu.be/EKCQ6sxMWNo)     

Indent란 기존 A라는 액티비티에서 B라는 액티비티(화면)으로 이동함    
각각 주어져있을 때 텍스트를 옮겨갈 수 있는 예제도 해봄  

이번 실습에서는 화면이 두개가 있어여 A에서 B로 이동할 수 있으므로   
MainActivity.java가 두개 필요함!    
<img src="/assets/img/posts/Cap 2020-10-24 05-36-22-.jpg">  
SubActivity.java를 생성하면 activity_sub.xml이 자동 생성됨.      


### 총정리 
Main화면에서 글을 적음.     
이동버튼을 누름     
Intent에 의해 화면이동이 되지만,    
putExtra에 의해 데이터가 넘어감.    

Sub화면에 도착함    
받은게 getIntent    
getIntent로 받고, String 데이터로 썼었으니까 getStringExtra로 받음      
마지막으로 메인화면에서 적은 글을 tv_sub 을 Sub화면에 쓰게함

<img src ="/assets/img/posts/Cap 2020-10-24 06-05-44-036.jpg">

MainActivity.java   
```java
package com.example.study1;

import androidx.annotation.Nullable;
import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {

    private Button btn_move;
    private EditText et_test;
    private String str;

    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        et_test = findViewById(R.id.et_test);
        btn_move=findViewById(R.id.btn_move);
        btn_move.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                str = et_test.getText().toString(); //EditText 입력폼에서 받아온 텍스트가 Sub화면에 출력됨
                Intent intent = new Intent(MainActivity.this , SubActivity.class ); //첫번째 인자는 현재 액티비티, 두번째는 이동하고 싶은 액티비
                intent.putExtra("str", str);
                startActivity(intent); //액티비티 이동


            }
        });
    }
}
```

SubActivity.java
```java
package com.example.study1;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.widget.TextView;

public class SubActivity extends AppCompatActivity {

    private TextView tv_sub;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_sub);

        tv_sub = findViewById(R.id.tv_sub);

        Intent intent = getIntent();
        String str = intent.getStringExtra("str");

        tv_sub.setText(str);


    }
}
```


activity_main.xml   

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">


    <EditText
        android:id="@+id/et_test"
        android:layout_width="200dp"
        android:layout_height="wrap_content"/>
    <Button
        android:id="@+id/btn_move"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="이동"/>

</LinearLayout>
```

activity_sub.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".SubActivity">


    <TextView
        android:id="@+id/tv_sub"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="30sp"
        android:text="서브 액티비티 이동"/>
</LinearLayout>
```
