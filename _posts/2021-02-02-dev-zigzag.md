---
layout: post
title: "2차원 배열의 지그재그 순회"
subtitle: ""
categories: dev
tags: til
comments: true
date: 2021-02-01 23:01:00 -0400
---

지그재그 순회의 수도코드를 살펴보자.
 
int i;
int j;

for i from 0  to n-1
	for j from 0 to m-1
		Array[i][j+(m-1-2*j)*(i%2)];
 
그러나 위와 같은 코드는 실전에서 생각날 리 만무하고,  
좀 더 구현하기 쉬운 코드를 익히는 게 좋겠다.  

아래에 첨부한 코드는 짝수행은 우측으로,  
홀수행은 좌측으로 순회한다.  


```java
import java.util.Scanner;

public class zigzag {
	public static void main(String[] args) {
		int n = 3;
		int m = 4;
		int num = 0;
		Scanner sc = new Scanner(System.in);
		int[][] map = new int[n][m];
		
		for(int i=0;i<n;i++) {
			for(int j=0;j<m;j++) {
				map[i][j] = sc.nextInt();
			}
		}
		
		for (int i = 0; i < n; i++) {
			if (i % 2 == 0) {// 짝수행
				for (int j = 0; j < m; j++) {
					System.out.print(map[i][j]+" ");
				}
			} else {// 홀수행
				for (int j = m-1; j >= 0 ; j--) {
					System.out.print(map[i][j]+ " ");
					
				}
			}
			System.out.println();
		}
	}
}
```