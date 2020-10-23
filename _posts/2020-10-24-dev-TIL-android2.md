---
layout: post
title: "안드로이드 강의2"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2020-10-24 01:23:00 -0400
---

## EditText와 Button
[홍드로이드님 안드로이드 강의 #2](https://youtu.be/mlxhD7M8Nsg)


### activity_main.xml 파일

empty project 만들기        
activity_main.xml : 정적인 부분. 화면 구성 등   
MainActivity.java : 동적인 부분     

EditText와 Button을 생성하고 각각 id를 부여함   
EditText에 hint로 흐린 글씨를 미리 보여줌       
Button에 text로 버튼 안에 글자 출력     

### MainActivity.java 파일  
EditText et_id; 
Button btn_test;    
와 같이 변수를 생성해주고 Alt Enter로 클래스를 import함 
onCreate로 처음 실행할 때 어떤 동작을 할지 정해줌   
여기서 et_id = findViewById(R.id.et_id);로 xml에서의 et_id와 연결해준다.    
동일하게 btn_test도 연결해줌.   

btn_test.setOnClickListener로 버튼을 클릭했을 때 입력칸에 액션을 취하게 해줌    
et_id.setText에 원하는 텍스트를 넣음.   



```java
package com.example.study1;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {


    EditText et_id;
    Button btn_test;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        et_id = findViewById(R.id.et_id);
        btn_test = findViewById(R.id.btn_test);

        btn_test.setOnClickListener(new View.OnClickListener() { //Alt Enter로 implement methods
            @Override
            public void onClick(View v) {
                et_id.setText("app study2"); //버튼을 클릭했을 때 텍스트박스에 텍스트가 뜨게 함
            }
        });

    }
}
```

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
        android:id="@+id/et_id"
        android:layout_width="300dp"
        android:layout_height="wrap_content"
        android:hint="아이디를 입력하세요..."/>

    <Button
        android:id="@+id/btn_test"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="버튼"/>

</LinearLayout>
```