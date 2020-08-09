---
layout: post
title: "OS summary"
subtitle: "운영체제 10판. cheeting sheet"
categories: review
tags:  os review book
comments: true
date: 2020-08-04 11:57:00 -0400
---

## 1장 서론
### 1.1 운영체제가 할 일
- 역할 : 하드웨어를 관리, 프로그램 수행을 제어하는 일   
사용자관점 : 용이     
시스템관점 : 자원할당자(리소스관리), 제어프로그램(장치관리, 오류보고)
- 컴퓨터시스템의 구성   
하드웨어 : CPU, 메인메모리, 스토리지, io장치  
소프트웨어 : 스케줄링하고 오류를 보고함.    
- 운영체제 정의     
os=커널=핵심적인 파트, 컴퓨터시스템이 동작하려면은 반드시 수행되어야 되는 프로그램.     
커널 외 프로그램은 시스템 프로그램과 애플리케이션 프로그램으로 나뉨.    
응용프로그램 : 사용자 목적에 맞춰서 씀.    
시스템 프로그램 : 시스템을 효과적으로 사용할 수 있도록 지원해주는 응용 레벨의 프로그램.     
파일관리, 프로그램 랭귀지 관리, 프로그램 로딩/실행 등.  
하드웨어에 접근하는 프로그램이기 때문에 시스템콜이 자주 발생    

핵심문장 : 프로그램을 수행하려면 디스크로부터 읽어들여서 메인메모리에 로딩해야함

### 1.2 컴퓨터 시스템의 구성
### 1.2.1 인터럽트
io연산과 cpu프로그램 수행이 동시에 진행(DMA)되기 때문에      
io연산이 종료됨을 cpu에게 알리기 위한 메커니즘.     
장치컨트롤러의 로컬버퍼에서, 데이터를 메인메모리로 이동 
- 과정 : 인터럽트 발생  
무조건적으로 해당 인터럽트 서비스 루틴을 실행.  
인터럽트 벡터(테이블)에서 주소색인.    
기존에 수행됐던 프로그램 잠시 중단.     
인터럽트 핸들러 루틴이 종료되면 중단된 위치로 복귀해야함.   
**10p그림**

### 1.2.2 저장장치 구조
계층적  
**14p그림**     
캐시 : 빠른 스토리지 매체에 있으면 사용, 아니면 스토리지에 접근.    

### 1.3 컴퓨터시스템 구조
- 멀티프로세서-장점 : 스루풋 증가, 경제적(메모리 공유), 신뢰성 높음(고장나면 다른 코어)     
- ASMP : master가 지시하고, slave는 자신만의 메모리만 실행가능 relationship)     
SMP : 프로세서간 master-slave관계가 없다. 그리고 많은 경우 메모리는 여러 프로세스간에 공유돼서 사용된다 .
- SMP는 크게 두 가지    
UMA : 동일한 메모리 액세스타임을 가짐. 어떤 위치에서 접근해도 보임.    
NUMA : 메모리 위치에 따라 달라짐.   


### 1.4 운영체제의 작동
- 멀티프로세서  : 여러개의 CPU 가 사용되는 시스템   
- 멀티코어 : CPU칩에 여러개 CPU 코어가 내포되는 경우.   

사실상 거의 모든 시스템은 이제 다중코어지만 컴퓨터 시스템의 단일 계산 단위를 가리킬 때는 일반적인 용어인 CPU 를 사용하고 하나의 CPU 에 존재하는 하나 이상의 코어를 구체적으로 언급할 때 코어와 다중 코어 용어를 사용한다. (p19)

- cpu 스케줄링 : 여러개의 프로그램이 동시에 수행될 수 있음.     
그러나 cpu는 하나. cpu에게 어떤 잡을 할당할 것인지 결정.    
- 잡 스케줄링 : 여러개의 잡을 수행하려면 그 잡들이 모두 메모리에 로딩되어야함.      
메모리는 한정되어있기에 어떤 잡들을 메모리로 올릴 것인지 결정하는 것.   
- 스와핑 :  프로그램을 실행하려면 무조건 메모리로 로딩해야함.   
그러나 현재 메모리에 다른 프로그램들이 꽉 차있다면 메모리로부터 디스크로 특정 잡을 쫓아내야 함.     
그리고 새로운 잡을 디스크에서부터 메모리로 로딩을 해야함.   
디스크로 로딩하는 잡을 스왑인, 메모리에서 디스크로 쫓아내는 것을 스왑아웃이라함.    
- 버추얼 메모리 :  여러개의 프로그램이 실행중일 때, 실행중인 많은 프로그램들이 메모리로 반드시 로딩될 필요는 없다.      
따라서 CPU가 보는 주소공간, 사용자가 보는 주소공간은 실제 피지컬 메모리의 주소공간보다 클 수 있음. 
따라서 버추얼 메모리라는 개념이 도입되었는데 피지컬메모리 즉 실제 사용되는 메모리보다 더 많은 공간을 쓰기 위해 사용자가 보는 주소공간을 버추얼 메모리라고 명명한다.     
- 프로세스 : 현재 번갈아가면서 수행되는 모든 잡들을 프로세스라고 함.    
- 인터럽트 분류 : HW인터럽트, SW인터럽트는 트랩이라고 하고 익셉션, 시스템콜이 있다.          
- 듀얼모드 : os를 에러로부터 보호하기 위해 유저모드, 커널모드로 실행    
- 모드비트 : 0이면 커널모드로 실행, 1이면 유저모드. 시스템콜이 호출되면 커널모드로 진입     

## 2장 운영체제 구조
### 2.1 운영체제 서비스
-  프로그램 수행, HW 관리   
- 사용자관점에서 기능   
파일시스템 관리-파일시스템 접근이나 파일탐색기  
소통-현재 수행중인 프로그램과의 소통제공    
에러보고-접근권한이 없는 리소스에 대한 경고 
- 효율성측면에서 기능   
자원할당    
accounting-HW를 어떻게 쓰고 있는지. ex) 작업관리자  
protection-HW가 어떻게 접근되는지.  
security-접근권한제어   
### 2.2 사용자와 운영체제 인터페이스
- 유저 인터페이스 : CLI커맨드라인, GUI그래픽, Batch리눅스나 쉘프로그래밍.   
~~정처기 표추가~~     
### 2.3 시스템콜
- 시스템 콜 : OS역할 중 HW관리.     
응용프로그램이 HW에 접근할 일이 있을 때 호출.   
라이브러리에 포함됨.
- 커널로 진입하기 : HW인터럽트(비동기적)나 SW인터럽트인 트랩(동기적, 익셉션과 시스템콜) 을 사용해야함.  
- 라이브러리 함수를 통한 간접호출 : 이식성, 프로그래밍 쉬워짐.  
- 시스템콜 인터페이스 : 테이블에 넘버와 시스템콜 함수가 담김. 효율성.   
- 리눅스에서 파라미터 전달 : 인자의 갯수가 6이하-인자값을 레지스터에 저장함 / 6초과-인자가 저장된 주소값저장 
- 시스템콜 예시:   

목적 | Windows | Linux
---------|----------|---------
 프로세스 제어 | CreateProcesS() | fork()
  - | ExitProcess() | exit()
  - | WaitForSingleObject() | wait()
 파일관리 | CreateFile() | open()
  - | ReadFile() | read() 
  - | WriteFile() | write()
  - | CloseFile() | close()
 장치관리 | SetConsoleModE() | ioctl()
  - | ReadConsole() | read()
  - | WriteConsole() | write()
  정보유지 | GetCurrentProcessID() | getpid()
  - | SetTimer() | alarm()
  - | Sleep() | sleep()
  통신  | CreatePipe() | pipe()
  - | CreateFileMapping() | shm_open()
  - | MapViewOfFile() | mmap()
  보호 | SetFileSecurity() | chmod()
  - | InitializeSecurityDescriptor() | umask()
  - | SetSecurityDescriptorGroup() | chown()


### 2.7 운영체제 설계 및 구현   
- 구현시 목표   
사용자관점 : 편리한사용, 배우기쉬움, 안정적작동, 빠르게수행.  
시스템관점 : 모듈화, 설계, 에러적게
- 팔라시 : 무엇을 할거야? 목적이 뭔지.     
매커니즘 : 어떻게 할거야? 목적을 달성하기 위해 어떤 기법을 썼는지.  
- 설계원칙 : 팔라시가 바뀌더라도 os 내부 메커니즘은 불변.(마이크로 커널. ex) 마크os)    
### 2.8 운영체제 구조
1. 모놀리틱 커널 : cpu-메모리-파일시스템-io장치 관리를 다 넣은 커널. 가장 간단한 구조. 아예 안 쓰임.
2. 계층구조(상부에서 하부접근가능, 디버깅과 작성쉬움), 
3. 마이크로커널 : cpu관리만 커널에. 나머지는 모두 유저모드로 올림. 확장성, 이식성 좋음. 프로세스 갯수 많아짐. 커널의 많은 기능이 유저레벨에 있음, 메시지패싱 오버헤드가 큼), 
4. 모듈구조(기능적으로 모듈화)    
- 리눅스는 기본적으로 계층구조, 추가적으로 모듈구조.      
### 2.9 운영체제 빌딩과 부팅    
- 시스템부트 : system generation-시스템이 어떻게 설정되는지 세팅하는 과정. SYSGEN program.
- 부트스트랩 로더 : ROM에 저장됨. HW초기화, 커널을 메모리로 로딩, 커널에게 제어권 넘김.
- 싱글스텝접근법 : 부팅되자마자 제어권이 부트스트랩 로더로 감.  
투스텝접근법 : 부트블럭을 하나 둠.(코드와 할일이 많아서)

가상머신 : 도입된 계기- 하나의 HW에서 다양한 OS를 동시에 사용.  
장점 - 부팅, sw개발시간 절약(테스트 용이), HW장비값 절감.     
단점 - 구현어려움. 각 os는 hw를 자신의 것인양 사용.       
가상머신 핵심 : virtualization layer. 하부 가상레이어에서는 커널을 프로세스로 여김.

## 3장 프로세스 관리
### 3.1 프로세스 개념
이 책에서는 프로세스,잡,태스크를 통용하여 말한다.   
- 프로세스 :  현재 실행중인 프로그램.   
프로그램보다 더 많은 자료구조가 필요. (주소공간이 필요함.)  
dynamic entity. 
- 프로그램 : 단순히 디스크에 저장된 프로그램. 정적인 엔티티     
- 프로세스 주소공간 : 스택-지역변수나 함수인자, 힙-동적메모리할당, 데이터-전역변수나 정적변수,초기화o&x변수, 텍스트-코드    
- PCB : program control block. 메모리로 로딩될때 필요함 
- 프로그램 카운터 : cpu내 레지스터가, 다음에 실행될 연산의 주소를 가짐. 

### 3.1.2 프로세스 상태
~~121p그림~~
- 프로세스 스테이트 : 프로세스는 active한 엔티티, 상태가 계속 변함.
- 뉴 : 프로세스 생성시점
- 러닝 : cpu가 해당p를 수행중
- 웨이팅 : p가 기다리는 상태. io요청이나 자체슬립상태, 다른p에서 오는 메시지 대기 등..
- 레디 : p는 실행가능상태. cpu가 수행못하는 중.
- 종료 : p가 수행끝     
</br>   
- 스케줄러 디스패치 : 레디->러닝
- 러닝에서 io요청받거나 이벤트wait : 러닝->웨이팅
- 웨이팅에서 인터럽트 끝났거나 이벤트 완료 : 웨이팅->레디
- 러닝에서 다른p에 밀리면 : 러닝->레디

### 3.1.3 프로세스 제어블록(PCB)
- PCB : 프로세스 상태, 프로그램 카운터, CPU레지스터들, CPU스케줄링, 메모리관리, accounting,입출력상태 정보를 저장함     
- 리눅스에서 PCB : task_struct 구조체형으로 관리함
- 프로그램카운터는 컨택스위치 발생시 문맥을 저장한다. 나중에 다시 돌아오기 위해

### 3.2 프로세스 스케줄링
- 멀티 프로그래밍의 목적 : CPU이용 최대화. 항상 어떤 프로세스가 실행되도록.     
- 잡큐(모든 프로세스의 집합), 
- 레디큐(레디상태인 태스크들) 
- 디바이스큐(io연산을 위해 대기중인 태스크들).  
</br>   
- 웨이팅 상태에 있으면 절대 스케줄링 안됨. 
- 레디큐에서 하나의 프로세스를 선택=스케줄링.
- 프로세스를 메모리로 로딩 = 잡큐에서.
- io bound process : io연산을 많이함, cpu연산적음. 우선순위 높다.
- cpu bound process : cpu연산많음, io연산은 짧음.
</br>
- degree of multiprogramming : 메모리에 있는 프로세스의 갯수를 의미함.  
많으면 시스템 불안정. 느려지고 프로세스 죽기도 함. 안정성의 요소.   
- 숏텀 스케줄러를 주로 사용.    
미디어텀 : 어떤 프로세스를 스와핑할지 결정하는 스케쥴러

### 3.2.3 문맥교환(context switch)  
- 컨택스위치 : p0->p1. p0정지 pcb0에 상태 저장, pcb1 복원. 그리고 p1실행
pcb1에 상태저장, pcb0 복원. 그리고 p0실행
~~127p그림~~
- 순수한 오버헤드가 큼. 줄여야함    
</br>   
- 회사별 예시
썬울트라스팍 : 레지스터를 여러 셋으로 두어서 관리   
암아키텍트 : 로드 앤 스토어 연산(여러 주소에 걸친 레지스터값을 하나의 연산으로 스토어함)

### 3.3 프로세스에 대한 연산
- 프로세스구조 : 트리형태. 조상프로세스에서 생성, 모든p는 pid가짐
- 프로세스 생성시 이슈  
리소스쉐어링(부-자 일부공유)       
실행옵션(병렬적으로 시행, 대부분 자식이 종료되길 wait)      
주소공간공유?(fork로 자식 생성, 자식은 exec로 변신, 부모는 wait)     
**이부분 심화학습하기 vfork함수**
</br>   
- fork : call once return twice. 리턴값으로 구분. 자식0 부모는 자식의 pid   
- 좀비 : 자식은 종료, 부모가 wait 안함.     
- 오펀 : 부모가 wait 대신 exit. 자식 러닝중. init이 입양함  
- 프로세스종료 : exit(자기자신을), abort(자식을). 종료하면 os는 리소스 회수.    
- abort : 자식이 할당된 리소스보다 오버했을때, 더이상 필요없을때.   

### 3.4 프로세스간 통신
- IPC : interprocess communication 
- cooperating process : 다른 p들과 영향을 주고 받는 여러p들이 병렬적으로 수행해서 하고자 하는 일을 달성 
- independance process : 다른 프로세스에 영향을 안 받는 프로세스
- 장점 : 정보공유(파일 하나오픈, p들이 공유), 계산가속화(서브태스크로 나눠서 계산시킴), 모듈성(별도의 임무부여)  
- 난점 : 각 p들은 자신만의 주소공간을 가짐. 다른 p들의 주소공간 못봄. 커널의 도움 필요.     
</br>   
- 커널에서 제공하는 메커니즘 : 공유메모리, 메시지전달
- 메시지전달 : 커널 내부에 메일박스 obj. send, receive. 커뮤니케이션 링크 설정.     
직접 : 발신시 수신자 명세. 문제점-코드에 pid명세. 하드코딩. e.g.파이프     
간접 : 중간에 링크인 메일박스가 존재. 자유롭고 보편적. 두개의 프로세스간에 여러개의 링크를 공유할 수 있다는 것. 프로그래밍 쉬움, 동기화 신경x. 컴퓨터간 소통시 사용(메모리 공유불가능), 작은양의 데이터 전송시.     
- 구현 : 메일박스 생성, send, receive, destroy
blocking send : 송신p는 메시지가 수신p나 메일박스에 의해 수신될떄 까지 블락됨
nonblocking send : 도착 하든 말든 송신p는 메시지 보내고 작업수행. email
blocking receive : 메세지가 이용가능할떄까지 p는 waiting상태에 멈춰있고 메시지를 받으면 작업시작
nonblocking receive : 송신p가 유효한 메시지나 null을 받음. zero capacity    
</br>   
- 공유메모리 : 특정 p의 주소공간 중 일부영역을 shm으로 설정.    
동기화필요.     
스핀락 많이쓰임.    
shmget 공유영역설정(shmat, shmdt, shmget)   
처음/끝에만 시스템콜 사용-빠름.     
protection메커니즘 필요. 빠르게 많은 양 공유시.     
</br>       
- 생산자-소비자 유한버퍼문제 : 버퍼가 공유공간. in포인터는 empty, out포인터는 full.

## 4장 스레드와 병행성
- 스레드 : 프로세스 생성은 리소스가 많이 필요하고 컴퓨팅자원을 많이 소모하며 오래걸림.  
스레드는 보다 적은 오버헤드가 걸린다.   
- 멀티스레딩 : 
하나의 프로세스 내에 여러개의 스레드가 병렬실행가능.    
공유할 건 공유하자. 코드/데이터 공유가능. 레지스터/스택 별도로. 
- 멀티스레딩의 장점     
    -  응답성 : 특정 스레드가 블락되더라도 해당프로세스에서는 실행가능하도록.  
하나가 고장나도 다른게 수행.     
    - 자원공유 : 스레드가 속한 프로세스의 자원과 메모리를 공유함.     
같은 주소공간 내 다른 작업을하는 스레드가능     
    - 경제성 : 프로세스는 생성시 메모리와 자원할당의 비용이 큼.       
스레드 생성 30배, 스레드간 컨택스위치 5배빠름.   
    - 규모적응성 : 멀티프로세서에서 각각의 스레드가 다른 프로세서에서 병렬로 수행가능함.      

### 4.2. 다중코어프로그래밍
- concurrently(병렬성) : 싱글코어 엑시큐션. 한시점에서는 하나의 태스크만 수행중
- parallelism(병행성) : 멀티코어-멀티프로세서 시스템이 concurrent를 효과적으로 쓸 수 있다.
~~179페이지~~       

### 4.2.1 도전과제
태스크 인식 : 독립된 병행가능태스크로 나누는 작업   
균형 : 전체 작업에 균등한 기여도를 갖도록      
데이터 분리 : 데이터를 태스크에 어떻게 분배할지     
데이터 종속성 : 다른 코어에서 쓰이는 스레드와 의존성검사     
테스트와 디버깅  : 어려움  

### 4.3 다중스레드모델
커널스레드 : 커널 내부에서 생성,해제됨. os에 의해 관리됨    
유저스레드 : 커널과 관계x. 라이브러리에서 생성됨    
커널-유저 매핑 :  스케줄링 하는 엔터티는 커널스레드.    
원칙 : 스케줄러는 유저 스레드의 존재를 모른다 유저스레드는 반드시 커널스레드에 맵핑이 되야함.     
커널스레드가 블락되면 맵핑된 유저스레드 세개도 동시에 블락됨.   
각각의 커널스레드가 서로 다른 p에 할당이 될 수 있음.    
유저스레드는 p에 할당x  
</br>   
- 모델 종류     
    - 매니투원 : 여러개의 스레드가 하나의 커널스레드에 맵핑.  
매우 빠르고 오버헤드가 적음.    
유저스레드는 라이브러리에서 만들어서.   
단점 - 커널스레드 죽으면 다죽음. 다중코어 이점없음.
    - 원투원 : 하나 블락되도 다같이 죽진않음.   
 유저스레드 생성마다 커널스레드 만들어져야해서 오버헤드큼.  
 생성횟수에 제한있음.
    - 매니투매니 : 멀티플렉싱 필수.복잡함.    
원투원과 매니투원의 장점혼합.   
원투원에서 생성횟수 제한극복.   
매니투원에서 멀티프로세싱이점 얻음.      
블락되어도 다른유저스레드로 할당돼서 수행가능함.        
스케줄러 액티베이션 메카니즘.   
    - 투레벨 : 매니투매니 + 원투원.     
 어떤 유저스레드는 매니투매니, 어떤 유저스레드는 커널원투원에 속함.     
 두 모델을동시에 씀.    
 원투원인 유저스레드는 바운드쓰레드라고 함.
</br>    
- 리눅스와 윈도우는 원투원모델을 사용.      
- 쓰레드가 생성이 될 때마다 별도의 PCB가 할당.  
별도로 다중프로세스에게 할당될 수 있는 객체.    
리눅스에서의 커널스레드는 백그라운드에서 실행하는 스레드.   

### 4.4 스레드 라이브러리
- 리눅스 pthread.h :create, init, join(wait함수처럼, 특정 th가 종료되길 기다리는 함수), exit    
int pthread_create(pthread_t* tid, pthread_attr_t *attr, (void8) f, void * arg);    
int pthread_join(pthread_t tid, void *thread_return); //넘길때 메시지   
int pthread_exit(void *thread_return); //남길 메시지    
</br>   

### 4.5 암묵적 스레딩
- 스레드 풀 : 생성되는 스레드의 갯수를 제한해서 시스템이 안정적으로 작동하게.(degree of multi programming).     
스레드 생성요청이 오면, 스레드풀에서 갖다씀.    
오버되면 못받던가 기다리던가.
- thread specific data : 각 전역변수를 특정 스레드에서만 쓰고자 한다.   
각 스레드가 자기만의 데이터를 쓸 수 있도록 지원해주는 메커니즘을 말한다.    
반드시 스레드 라이브러리에서 지원이 되야함  
- 피어스레드 : pthread create 함수를 호출해서 피어스레드를 생성함.  
그때부터 피어스레드와 메인스레드는 동시에 실행이 되고 있음

### 4.6 스레드와 관련된 문제들
- fork이슈 : 하나의 프로세스내에 여러개 스레드. 모든 스레드를 카피해서 사용.    
- 종료이슈 : 남아있는 스레드를 타겟 스레드.        
    - 비동기식 취소-한 스레드가 즉시 타겟스레드를 강종시킴.    
    - 지연취소-안전한 지점이라고 여겨질때까지 캔슬을 지연함.    
    타겟스레드가 주기적으로 자신을 체크함.   
- 시그널처리
    - 싱크러너스-에러발생시 알려줌. 익셉션핸들러    
    - 어싱크러너스 - 외부에서 발생되는 이벤트일경우 유저디파인핸들러 호출.  
- 시그널을 어떤 스레드에 전송?  
    - 적용된 단일스레드(0으로 나누는 익셉션)    
    - 프로세스내 모든 스레드(프로세스 킬)
    - 특정 스레드 그룹
    - 명세된 스레드(pthread kill)   

## 5장 CPU 스케줄링
### 5.1 기본개념
### 5.1.1 CPU-I/O 버스트 사이클
- cpu버스트 : CPU가 해당 프로세스를 수행하는 것     
- io버스트 : 디스크 IO 나 디바이스 IO를 수행하는 버스트 
- cpu-bound 프로세스 : 대표적인 예는 복잡한 수학연산, 혹은 비디오 디코딩과 같이 연산양이 많은 프로세스를 의미      
- io-bound 프로세스 : 워드프로세스 와 같이 IO 연산이 계속됨.    
키보드에서 입력받고 저장하는 일을 많이 하는 워드프로세싱 작업 같은 경우. 우선순위 높음.   

### 5.1.2 CPU 스케줄러
- cpu스케줄러 : 현재 레디 상태에 있는 프로세스 중 하나를 선택해서 씨피유를 해당 프로세스에게 할당하는 할당하는 과정.    
- 스케줄링 디시전 :     
    1. 러닝->웨이팅 : 러닝이 공석. 레드큐에서 선택해서 러닝으로    
    2. 러닝->레디 : 러닝이 공석. 레디큐에서 선택해서 러닝으로  
    3. 웨이팅->레디 : 레디로 바뀐게 우선순위 높으면 선점해서 러닝으로.     
    4. 러닝->터미네이션 : 러닝이 공석. 스케줄링 디시전  
    - 1.4가 비선점적. 자발적으로 전이한 경우.     
    - 1,2,3,4는 선점적    

### 5.1.3 선점 및 비선점 스케줄링
- 선점스케줄링 : 기존에 수행됐던 프로세스가 안 끝났더라도 우선순위가 높은 태스크가 도착하면 그걸 수행.  
기존의 시행됐던 문맥을 저장을 해야함.   
shared data access이슈   
- 비선점스케줄링 : 자발적으로 CPU를 놓았느냐 안 놓았느냐.   
러닝에서 웨이팅or터미네이션 
- 시스템콜 발생시 : pa가 시스템콜 호출, 우선순위 높은 pb가 레디상태.    
커널내에서 시스템콜이 수행중이어도 선점을 허용해서 pb가 먼저 수행됨(선점적커널).    
pa의 시스템콜이 끝나고 pb가 실행되면 비선점적 커널  
오래된 버전의 유닉스 계열은 대부분 비선점적 커널.   
버전 2.6부터는 선점커널.    
최근에는 리얼타임 컴퓨팅 수요가 많아짐에 따라 선점적 커널을 채택    
- 하드웨어 인터럽트 발생시 : 핸들러가 커널 내에서 수행되었을 경우, 우선순위 높은 테스크가 레디상태로 바꼇다고 생각해보자.   
선점커널이든 비선점커널이든 허용을 안함.    
인터럽트 핸들러는 빠르게 무조건적으로 수행되야하기 때문이다.    
### 5.1.4 디스패처
- 디스패처 : 선택이 되고 나서 새로운 프로세스로 수행을 넘기는 과정. (레디->러닝)    
기존에 수행됐던 테스트 문맥을 저장->새로운 프로세스의 수행을 위해서 유저모드로 전환->   
새로운 프로세스의 수행을 시작하는데까지 디스패쳐가 일을 수행    
- 디스패치 레이턴시 : 스케쥴링 결정이 내려지고 나서 새로운 프로세스의 인스트럭션이 수행되기까지 걸리는 시간. 연산 비쌈.     

### 5.2 스케줄링 기준 : 
- cpu utilization(일한시간/일한시간+유휴시간)     
- throughput(특정시간유닛 내에 실행완료한 프로세스의 갯수)    
- turnaround time(프로세스가 끝나는 시간에서  프로세스가 처음에 제출된 시간을 뺀다)   
- waiting time(레디큐에서 기다린 총 시간)       
- response time(리퀘스트가 제출되고 나서 첫 번째 응답이 산출될 때까지 걸리는 시간)    
- 턴어라운드 vs 웨이팅타임 : 로딩부터 프로세스 끝날때까지 / 레디큐에서 기다린 시간  
- 리스폰스 vs 웨이팅 : 첫번째 cpu burst까지 걸린 시간 / 레디큐에서 기다린 시간    
- 시스템 전체에 적용 : utilization, throughput. 평균, 분산 안 중요. 각각 최대화 하면 좋음 
- 개별 프로세스에 적용 : turnaround, waiting, response. 평균 waiting time 최소화, 평균 response 최소화, 프로세스간 waiting time 분산을 어떻게 처리할건지  

### 5.3 스케줄링 알고리즘
### 5.3.2 FCFS Scheduling 
- first come first served. waiting time 계산, 평균 waiting time계산. 간트차트.     
- convoy effect : 짧은 p가 긴 p뒤에서 기다리는 경우   

### 5.3.2 SJF Scheduling
- 가장 짧은 cpu burst를 갖는 p에게 우선순위 높게. 
    - SJF 비선점 : p1수행중, p2가 도착했고 더 짧더라도 p1이 끝나길 기다림 
    - SJF 선점(SRTF shortest remaining time first) : p1수행중, p2가 도착했고 p1남은 시간보다 p2가 짧으면 p2수행   
- SJF is optimal : average waiting time최소화 측면에서 최적임. 평균 waiting time과 turnaround time계산  
</br>   
- exponentioal evarage기법 : 최근의 히스토리에 보다 높은 가중치를 둔다.   
</br>

### Round-Robin Scheduling
- time quantum : tq가 만료되면 수행을 멈추고, 레디큐 맨끝에 추가됨.  
선점된 t가 시작됨.   
- 레디큐에 n개있고 tq 가정. 최대 기다리는 시간은 (n-1)* tq. 기아 안일어남.    
큐의 맨 끝에 있을 경우 n-tq타임유닛으로 최악 waiting time이 보장됨.     
- tq가 너무 커서 무한대일경우 FIFO와 같아진다.    
반대로 너무 짧으면 컨택스위치 많아져서 오버헤드 커짐.   
- SJF보다 waiting,turnaround 측면에서 안 좋음.     
response측면에서 좋음.  
- 컨택스위치의 횟수와 리스폰타임에 트레이드오프 관계.  

### 5.3.4 priority Scheduling
- 문제점-기아발생.    
    - 우선순위 높은 t가 계속 레디상태면 낮은건 무한정대기 걸림.    
    - 해결책-우선순위를 점진적으로 바꿔주는 aging기법(dynamic priority palacy).   
- static priority sheduling 은 우선순위 불변함

### 5.3.5 Multilevel Queue Scheduling
- 큐간에, 큐안에 스케줄링있음.    

### 5.3.6 Multilevel Feedback Queue Scheduling
- 멀티레벨큐와의 차이점 : 피드백큐는 프로세스가 큐간에서 움직이는 것을, migration하는 것을 허용  

### 5.4 스레드 스케줄링
유저스레드, 커널스레드 중에서 스케줄되는 대상은 커널스레드.
유저스레드는 스레드 라이브러리에 의해 관리되고, 커널은 이들의 존재를 알지못함. 
유저스레드는 연관된 커널스레드에 매핑되어야함.
- 경쟁범위
    - PCS : 프로세스 경쟁범위. 동일한 프로세스에 속한 스레드들 사이에서 CPU를 경쟁
    - SCS : 시스템 경쟁범위. 시스템상의 모든 스레드 사이에서 경쟁.  
    리눅스, 윈도우는 원투원모델이므로 SCS만 사용하여 스케줄함.

### 5.5 다중처리기 스케줄링(multiple processor scheduling)
- 코어가 여러개일때 스케줄링은 cpu가 여러개라서 할당이슈가 추가됨.  
SMP, ASMP(master-slave있음) 
거의 모든 최신 OS는 SMP를 지원한다.
- 전략 
1. 모든 스레드가 공통준비큐에 있을 수 있다.
2. 각 프로세서는 자신만의 스레드 큐를 가질 수 있다.

### 5.5.2 다중코어 프로세서(MultiCore Processors)
### 5.5.3 로드밸런싱
- 로드가 inbalance된 상황, 즉 특정 프로세스에 태스크가 몰리는 상황이 발생하면 migration해야한다.   
    - push migration : 특정 specific한 태스크가 모니터링한다. 각각의 프로세스의 로드는 어떤지. 로드 인밸런스가 발견되면 균등하게 분산시켜준다.  
    - pull migration : 아이들한 cpu가 다른 바쁜 프로세스에 있는 태스크를 가져온다. pull.    
### 5.5.4 처리기 선호도
- affinity : 프로세스간 친밀도  
        - soft : os가 affinit관계에 있는 cpu에게 할당하려고 노력은 하는데 보장은 못한다는 소리임    
        - hard : 프로그래머가 os에게 요청한 경우 보장되어야함.  
        프로그래머는 os에게 요청할 수 있는 시스템콜이 필요함

### 5.6 실시간 CPU 스케줄링
- POSIX 실시간 스케줄링 : 세개의 클래스로 나뉨.     
SCHED_FIFO SCHED-RR (리얼타임)  
SCHED_NORMAL(컨벤셔널)  

- 멀티레벨큐에서, 큐간priority-리얼타임 프로세스에서 하나를 선택.   
큐안CFS-컨벤셔널 프로세스에서 하나를 선택.
- 리얼타임이 컨벤보다 우선순위 높음.    
sched_fifo와 rr의 차이는, 타임퀀텀. 

### 5.7 운영체제 사례들
- 리눅스 스케줄링- CFS : completely fair scheduler.  
cpu할당 비율. 어느 시점에서도 이 비율이 보장.   
vruntime이 가장 작은 값에 우선순위를 높여서 수행하는 게 CFS 스케쥴링 방식이다.  
- vruntime 변수 : vruntime이 가장 작은 태스크를 다음에 스케쥴링한다.    
이전에 수행된 시간이 많으면 가능한한 다음에 수행하지 않기   

### 5.8 알고리즘 평가
Deterministic modeling 간트차트, 큐잉 모델, simulations

	


