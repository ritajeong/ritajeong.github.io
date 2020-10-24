---
layout: post
title: "안드로이드 강의4 ImageView & Toast"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2020-10-24 06:24:00 -0400
---

## Image View & Toast 
[홍드로이드님 안드로이드 강의 #4](https://youtu.be/fRDy13p8L78)     

### 이미지 넣고 정렬하기        
ImageView를 LinearLayout으로 감싸고, gravity="center"로 가운데 정렬해줬다. 주석참고         

<img src ="/assets/img/posts/Cap 2020-10-24 07-15-41-193.jpg">  

### 사진을 누르면 토스트 메시지 출력하기    
동적인 부분이기 때문에 MainActivity.java에서 
findViewById로 toast메시지의 아이디를 받아오고  
setOnClickListener로 메시지를 출력한다.     
<img src ="/assets/img/posts/Cap 2020-10-24 07-18-18-775.jpg">  


MainActivity.java   
```java
package com.example.study1;

import androidx.annotation.Nullable;
import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.media.Image;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.ImageView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    private Button btn_move;
    private EditText et_test;
    private String str;
    ImageView test;

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
                Intent intent = new Intent(MainActivity.this , SubActivity.class ); //첫번째 인자는 현재 액티비티, 두번째는 이동하고 싶은 액티비티
                intent.putExtra("str", str);
                startActivity(intent); //액티비티 이동
            }
        });

        test = (ImageView)findViewById(R.id.test); //test id를 찾아오는 과정
        test.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Toast.makeText(getApplicationContext(), "This is toast message", Toast.LENGTH_SHORT).show();
            }
        });

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

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center">

        <!--image view-->
        <ImageView
            android:id="@+id/test"
            android:layout_width="100dp"
            android:layout_height="100dp"
            android:src="@mipmap/ic_launcher" />
    </LinearLayout>
</LinearLayout>
```
