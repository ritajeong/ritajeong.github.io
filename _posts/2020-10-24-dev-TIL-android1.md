---
layout: post
title: "안드로이드 강의1"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2020-10-24 01:05:00 -0400
---

## TextView
[홍드로이드님 안드로이드 강의 #1](https://youtu.be/wZdImPoFjW8)


LinearLayout 사용하기   

Text view 다루기    
match_parent : 가로길이는 부모를 따라가기   
wrap_content : 폰트 사이즈만큼 감싸기   
text, textColor, textSize   

Textview 세 번 반복하려면   
android:orientation="verical" 추가  



```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">


    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="app study day1"
        android:textColor="#0004ff"
        android:textSize="20sp"
        />
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="app study day1"/>
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="app study day1"/>

</LinearLayout>
```

