---
layout: post
title: "안드로이드 강의7 Navigation menu"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2020-10-25 09:50:00 -0400
---

## Navigation menu     
[홍드로이드님 안드로이드 강의 #7](https://youtu.be/2yDa2KiY03s)    

이번 강의에서는 Navigation Drawer Activity 템플릿으로 새 프로젝트를 만들었다.   
나는 이전에 만들던 프로젝트에 Navigation Drawer Activity를 추가하는 식으로 만들어봤다.  


- MainActivity.java의 onNavigationItemSelected 함수에서   
아이콘을 클릭하면 취할 액션을 설정한다.     

- res/menu/activity_main_drawer.xml  
여기에는 drawer의 아이콘을 설정할 수 있다.  
title에서 아이콘 옆에 붙는 이름을 설정할 수 있다.   

문제점 : NavActivity.java 에 Navigation Drawer Activity를 생성했는데    
MainActivity.java에서 Intent를 어떻게 설정할 지 모르겠다.   
선택한 방법은 일단 강의를 더 듣기   
시간이 촉박한데 큰일이다 ㅠ


NavActivity.java
```java
package com.example.study1;

import android.os.Bundle;
import android.view.MenuItem;
import android.view.View;
import android.view.Menu;

import com.google.android.material.floatingactionbutton.FloatingActionButton;
import com.google.android.material.snackbar.Snackbar;
import com.google.android.material.navigation.NavigationView;

import androidx.annotation.NonNull;
import androidx.core.view.GravityCompat;
import androidx.navigation.NavController;
import androidx.navigation.Navigation;
import androidx.navigation.ui.AppBarConfiguration;
import androidx.navigation.ui.NavigationUI;
import androidx.drawerlayout.widget.DrawerLayout;
import androidx.appcompat.app.AppCompatActivity;
import androidx.appcompat.widget.Toolbar;

public class NavActivity extends AppCompatActivity {

    private AppBarConfiguration mAppBarConfiguration;

    @Override
    protected void onCreate(Bundle savedInstanceState) { //앱의 시작지점
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_nav);
        Toolbar toolbar = findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);

        FloatingActionButton fab = findViewById(R.id.fab); // 버튼을 띄우는 아이콘을 관리
        fab.setOnClickListener(new View.OnClickListener() { //선언
            @Override
            public void onClick(View view) { //fab을 클릭했을 때 snackbar가 나오도록
                Snackbar.make(view, "Replace with your own action", Snackbar.LENGTH_LONG)
                        .setAction("Action", null).show();
            }//람다로 쓰는 거 연습하기
        });//스낵바는 토스트랑 비슷한데 더 업그레이드 버전. 더 세련된 디자인의 팝업임

        //drawer layout은 리스트뷰를 왼쪽에서 꺼낼 때 씀
        DrawerLayout drawer = findViewById(R.id.drawer_layout);
        NavigationView navigationView = findViewById(R.id.nav_view);
        // Passing each menu ID as a set of Ids because each
        // menu should be considered as top level destinations.
        mAppBarConfiguration = new AppBarConfiguration.Builder(
                R.id.nav_home, R.id.nav_gallery, R.id.nav_slideshow)
                .setDrawerLayout(drawer)
                .build();
        NavController navController = Navigation.findNavController(this, R.id.nav_host_fragment);
        NavigationUI.setupActionBarWithNavController(this, navController, mAppBarConfiguration);
        NavigationUI.setupWithNavController(navigationView, navController);
    }

    @Override
    public void onBackPressed() { //뒤로 가기 버튼을 누를 때 아래 액션을 취함
        //뒤로 가기를 눌렀을 때 drawer layout을 찾아주고
        DrawerLayout drawer = (DrawerLayout) findViewById(R.id.drawer_layout);
        if(drawer.isDrawerOpen(GravityCompat.START)){ //열려있으면
            drawer.closeDrawer(GravityCompat.START);//닫기
        }else {
            super.onBackPressed(); //안 열려있으면 뒤로 가기.
        }
    }

    //앱을 시작할 때 옵션메뉴를 생성
    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.nav, menu); //만들어놓은 템플릿을 가져옴
        return true;
    }

    //옵션메뉴가 클릭되었을 때
    @Override
    public boolean onOptionsItemSelected(@NonNull MenuItem item) {
        int id = item.getItemId();

        //noinspection SimplifiableIfStatement
        if(id == R.id.action_settings){
            return true;
        }

        return super.onOptionsItemSelected(item);
    }

    public boolean onNavigationItemSelected(MenuItem item){
        int id = item.getItemId();
        //아이템 셀렉트가 이루어졌을 때 메뉴를 누르면 그 메뉴에 대한 액션이 이루어짐
        if(id==R.id.nav_gallery){

        }else if(id ==R.id.nav_gallery){

        }else if(id==R.id.nav_slideshow){

        }

        //drawer layout을 아예 닫아버리겠다
        DrawerLayout drawer = (DrawerLayout) findViewById(R.id.drawer_layout);
        drawer.closeDrawer(GravityCompat.START);
        return true;
    }

    @Override
    public boolean onSupportNavigateUp() {
        NavController navController = Navigation.findNavController(this, R.id.nav_host_fragment);
        return NavigationUI.navigateUp(navController, mAppBarConfiguration)
                || super.onSupportNavigateUp();
    }
}
```