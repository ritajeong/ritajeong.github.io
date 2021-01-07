---
layout: post
title: "안드로이드 강의5 패키지구조"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2020-10-24 22:35:00 -0400
---

## 패키지 구조 & 역학 
[홍드로이드님 안드로이드 강의 #5](https://youtu.be/Y3vZFe5fI9c)     

### AndroidManifest.xml 파일        
- 안드로이드에서는 기본 앱 설정을 할 수 있다.     
- icon=@mipmap/ic_launcer를 컨트롤 클릭 -> png파일 들어가기           
그러면 초록이 안드로이드가 기본 이미지로 돼있는 걸 볼 수 있다.  
그래서 앱 아이콘을 바꾸고 싶으면, drawble이나 mipmap폴더에 파일을 넣고, 경로를 써주면 된다.     
- label을 컨트롤 클릭   
app_name이 선언돼있음.  
- roundIcon : 아이콘의 테두리를 둥글게 해줌     
- theme : 컨트롤 클릭하면, 테마 색이 선언돼있는 걸 볼 수 있다.      
기본 지정되어있음.      
- activity  
java 폴더에서 액티비티를 extension 하는 걸 선언할 때는  
항상 manifest.xml에서 액티비티를 선언해야한다.  
SubActicity를 만들 때도 선언했었음.     
- activity에서 intent-filter    
액티비티가 메인이고, 런쳐임.    
런쳐 : 앱이 시작될 때 처음으로 시작되는 곳이 어딘지 지정해줌.      
intent-filter를 SubActivity부분으로 옮기면 처음 시작지점이 SubActivity가 될 것이다.     

### res 폴더    
- resource 폴더   
주로 이미지 폴더가 있다.    
- layout 폴더   
layout 파일들을 모아놓는 폴더   
미리 빌드하지 않아도 액티비티에서 보면서 수정할 수 있다.    
액티비티와 연결하는 레이아웃 파일들을 담당함    
- mipmap 폴더   
ic_launcer와 ic_launcer_round가 있음.       
처음엔 기본제공하는 이미지들이 있다.    
dpi가 여러가지가 있다.  : 폰마다 해상도가 다르기 때문에     

### values 폴더
colors.xml : 원하는 컬러를 선언해놓을 수 있다.  
RGB값에 이름설정 등     
strings.xml : 길어지는 문장이나 반복되는 문장을 선언할 수 있음  
styles.xml :  기본적인 앱테마나 활성테마를 만들어서 설정    



### AndroidManifest.xml 파일 소스코드

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.study1">
    <!--icon, label을 ctrl 클릭 : 해당 경로로 이동-->
    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Study1">
        <activity android:name=".SubActivity"></activity>
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```