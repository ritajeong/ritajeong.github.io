---
layout: post
title: "지그재그 순회"
subtitle: ""
categories: til
tags: til
comments: true
date: 2021-02-01 23:01:00 -0400
---

지그재그 순회  

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