---
layout: post
title: "순열과 조합, 중복순열과 중복조합"
subtitle: ""
categories: til
tags: 
comments: true
date: 2021-02-04 10:00:00 -0400
---

순열, 조합은 타겟 중심이다.  
순열은 재사용이 가능하고, 위치가 다르면 상관없다.  
소스를 반복적으로 사용할 수 있다. 
단, 중복순열이 아니니까 사용한 건 체크해야함.  
select 배열이 중간 지점을 체크한다.  
재귀함수를 호출한 뒤 다시 false로 초기화해야함.  

조합은 select배열이 필요없음.  
한 번 뽑히면 더 이상 뽑히지 않음.  
되돌아오지도 않음!  

부분집합은 소스중심. 사용여부가 중요하다.  
select배열이 최종적인 역할을 한다.  


순열, 조합, 부분집합에 대한 문제는 매일 풀어라.  
그만큼 중요한 부분이다.  
구구단 외울 때 처럼.. !  
그래야 응용문제가 나왔을 때 순조롭게 풀 수 있다.  

월요일부터 수요일까지는 2차원배열을 순회하는 부분을 배웠다면,  
이젠 새로운 단원을 시작한다고 생각하면 된다.  
주말에 순열, 조합, 부분집합에 대한 연습을 확실히 하자.  
손에 익을 정도로 !  


### 순열 
순열은 select[] 가 필요하다.  
먼저 선택됐다고 표시하고, 다음 선택으로 간 후에 선택하지 않았다고 표시한다.  
매번 모든 소스에 대해 고려한다.  
단, 현재 선택된 항목은 제외한다.
```cpp
for(int i=0;i<N;i++	){
	if(!select[i])
		{
			tgt[tgtIdx] = src[i];
			select[i] = true;
			perm
		}
}
```


### 조합  
select[]가 필요하지 않다.  
항상 선택하고 다음 선택을 한다.  
이전 선택을 제외한 소스에 대해 모두 진행한다.  

### 부분집합  
tgt[]가 필요하지 않다.  



```java
package com.ssafy.exhaustive;

import java.util.Arrays;
import java.util.Scanner;

public class DiceTest {
	static int N, M, totalCnt;
	static int[] numbers;
	static boolean[] isSelected;

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		N = sc.nextInt();
		numbers = new int[N];
		isSelected = new boolean[7]; // 1-6 주사위 눈의 사용여부

		int M = sc.nextInt(); // 던지기 모드
		totalCnt = 0;
		switch (M) {
		case 1:
			dice1(0);
			break;
		case 2:
			dice2(0);
			break;
		case 3:
			dice3(0, 1);
			break;
		case 4:
			dice4(0, 1);
			break;
		}
		System.out.println("총 경우의 수 : " + totalCnt);
	}

// 중복순열 nCr ==> n^r
	private static void dice1(int cnt) {
		if (cnt == N) {
			totalCnt++;
			System.out.println(Arrays.toString(numbers));
			return;
		}
		for (int i = 1; i <= 6; i++) {
			numbers[cnt] = i;
			isSelected[i] = true;
			dice1(cnt + 1);

		}
	}

//순열 : nPr ==> n! = (n * n-1 * n-2 ....) r개만큼 곱함. 
//6P3 = 6 * 5 * 4 = 120
	private static void dice2(int cnt) {
		if (cnt == N) {
			totalCnt++;
			System.out.println(Arrays.toString(numbers));
			return;
		}
		for (int i = 1; i <= 6; i++) {
			if (isSelected[i])
				continue; // 현재자리에 뽑힐 수 있는 수를 다음수로 선택한다. 111

			numbers[cnt] = i;
			isSelected[i] = true;
			dice2(cnt + 1);
			isSelected[i] = false;
		}
	}

	// 중복조합 : nHr
	// 6H3 : (n+r-1)Cr = 8C3 = 8 * 7 * 6 / (3 * 2* 1) = 56
	private static void dice3(int cnt, int start) {
		if (cnt == N) {
			totalCnt++;
			System.out.println(Arrays.toString(numbers));
			return;
		}
		for (int i = start; i <= 6; i++) {
			numbers[cnt] = i;
			dice3(cnt + 1, i);
		}

	}
	
	//조합 : nCr 
	//6C3 = 6 * 5 * 4 / ( 3 * 2 * 1) = 30
	private static void dice4(int cnt, int start) {
		if (cnt == N) {
			totalCnt++;
			System.out.println(Arrays.toString(numbers));
			return;
		}
		for (int i = start; i <= 6; i++) {
			numbers[cnt] = i;
			dice4(cnt + 1, i + 1);
		}

	}

}// 클래스 끝

```