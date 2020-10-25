---
layout: post
title: "안드로이드 강의8 SharedPreferences"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2020-10-25 11:10:00 -0400
---


## SharedPreferences
앱 종료하더라도 재 실행했을 때 남는 데이터값이나 저장되는 값이 그대로 남는 경우.    
이럴 때 주로 사용하는 함수이다.     

[홍드로이드님 안드로이드 강의 #8](https://youtu.be/-2QPmS4OWos)    
 
시나리오 : 앱 실행 - EditText 뜸 - 임의로 텍스트 입력 - 뒤로가기 버튼으로 앱 종료   

소스코드는 변경한 부분만 첨부했다.
MainActivity.java와 activity_main.xml부분이다.

```java
//onCreate 함수 부분
protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        et_save = (EditText) findViewById(R.id.et_save);
        //SharePreferences
        SharedPreferences sharedPreferences = getSharedPreferences(shared, 0);
        String value = sharedPreferences.getString("savedValue","");
        et_save.setText(value);
}


//onDestroy 함수 부분
@Override
    protected void onDestroy() {
        super.onDestroy();

        SharedPreferences sharedPreferences = getSharedPreferences(shared, 0);
        SharedPreferences.Editor editor = sharedPreferences.edit();
        //SharePreferences안에 에디터를 연결함
        String value = et_save.getText().toString(); //getText는 현재 써져있는 값을 받아와서 스트링으로 씀
        editor.putString("savedValue", value);
        editor.commit();
    }
```

```xml
    <!--sharedPreferences-->
    <EditText
        android:id="@+id/et_save"
        android:layout_width="200dp"
        android:layout_height="wrap_content"/>
```