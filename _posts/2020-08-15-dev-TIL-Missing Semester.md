---
layout: post
title: "Missing Semester by Cambridge"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2020-08-15 12:45:00 -0400
---

## Lecture 1: Course Overview + The Shell (2020)
[YOUTUBE LINK](https://www.youtube.com/watch?v=Z56Jmr9Z34Q&t=1763s)     
2019년 2학기에 유닉스 프로그래밍 수업을 들었었다.   
그 때 리눅스에서 쉘을 사용하는 방법을 배웠었는데, 최근 [깔끔한 파이썬 탄탄한 백엔드] 책을 읽으면서 다시금 커맨드를 리마인드해야겠다고 생각했다.     
유튜브 알고리즘으로 추천받은 채널이지만 학습에 매우 적합하다고 여겨져 이 자료를 선택했다.      
총 11강정도 되는 듯 하다.  
**이 강의목록의 메인 아이디어는 CS 이론에 앞서 IDE나 쉘 등의 tool을 유연하게 다루는 방법이다.**     
vim, git, debugging, security에 대한 강의는 다음에도 꼭 찾아서 들어야겠다.  
아래 링크는 올해 초에 진행된 lecture 소개 웹사이트이다.     
[Missing Semester](https://missing.csail.mit.edu/about/)

유튜브 강의를 보면서 타임라인으로 기록했고, 중간중간에 주요한 멘트들은 메모하면서 들었다.   

6:04 shall prompt   
6:32 curstermizing shall    
commands    
7:03 $date  
7:19 $echo  
7:29 $echo hello    
7:46 $echo "Hello world"    
    echo Hello] World   
8:41 how does the shall know what these progrmas are when I type date or when I type echo   
how does it know what these programs are supposed to do ?   
the answer to this is your computer has a bunch of built-in programs that comes with the machine    
10:01 environment variable  
10:17 $echo $PATH   
11:01 $ which echo  
12:30 relative path     
12:50 $pwd (print working directory)    
13:24 cd /home (change my directory)    
13:58 dot   
cd ..   
cd ./home   
15:03 ../../../../../   
relative path and absolute path 
16:20 $ls   
17:15 ~ tild    
$ cd ~  
17:36 - dash    
$ cd -  
18:20 help  
ls -l   
20:09 d means directory 
21:32 read, write, execute  
24:32 mv (rename, move)     
25:20 cp (copy from, to)    
25:50 rm (remove)       
26:15 rmdir, mkdir (remove directory, make directory)   
26:50 man (manual)  
27:55 Ctrl+L (clear shall)  
28:30 input and output  
29:30 $echo hello > hello.txt   
29:59 $cat hello.txt    
30:10 $cat < hello.txt  
30:43 $cat < hello.txt > hello2.txt 
$cat hello2.txt 
31:15 $>>^C 
31:50 pipe  
32:20 tail  
$tail -nl   
$ls -l / | tail -nl 
$ls -l / | tail -nl > ls.txt    
33:35 curl  
curl --head --silent google.com     
curl --head --silent google.com | grep -i content-length    
curl --head --silent google.com | grep -i content-length | cut --delimetr = ' ' -f2 

35:20 how to use the ternimal and a more interesting and perhaps more powerful way that you might be used to and this is perhaps even going to be interesting for the ones of you who feel like you're already comfrotamble with the terminal.  
bur first we need to  cover a important topic when it comes to linux systems and mac os in particular which is  the notion of root user.    
the root user is sort of like the administrator user on windows and it has user IDz zero.
the root user is special because it is allowed to do whatever it wnats on your system.  
even if a file is like not readable by anyone or if it's not writable by anyone root can still access that file.    
the root is sort of a super user that gets to do whatever they want.    
and  most of time you will not be operating as the super user.      
you will not be root.   
because you were operating your computer as the root user at all times if you ran the wrong program they could just completely destroy your computer and you don't want that.   
but every now and again you want to do something that requires that you are root, usually for these cases you will use a program called sudo    
36:39 $sudo (super user)    
38:02 $cat brightness
$sudo echo 500 > brightness

