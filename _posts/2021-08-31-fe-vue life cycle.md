---
layout: post
title: "Vue Life Cycle"
subtitle: ""
categories: frontend
tags: frontend
comments: true
date: 2021-08-31 07:33:00 -0400
---

# vue life cycle

- 총 8가지가 있다.

- 크게 4단계 : 생성-부착-갱신-소멸

  created-mounted-updated-destroyed

### 📌beforeCreate

data, methods속성이 아직 정의되지 않은 상태.

DOM에 접근 불가

### 📌created

data, methods속성이 정의됨. this.data나 this.fetchDate()와 같은 로직으로 접근 가능.

DOM에 접근 불가

### 📌beforeMount

created 단계 이후 template속성에 지정한 마크업 속성을 render()함수로 변환한 후 el속성에 DOM에 인스턴스를 부착하기 전에 호출되는 단계.

**render()함수가 호출되기 직전의 로직**

### 📌mounted

DOM에 인스턴스가 부착되고 나면 호출되는 단계.

DOM 접근 가능

**화면요소를 제어하는 로직**

주의) 부착되자마자 바로 호출되기 때문에 하위 컴포넌트나 외부 라이브러리에 의해 추가된 DOM요소들이 최종 HTML로 변환되는 시점과 다를 수 있음

### 📌beforeUpdate

인스턴스에 정의한 속성들이 화면에 치환됨

- 데이터 관찰 : 치환된 값은 $watch속성으로 감시

  데이터가 변경되면 가상 DOM으로 화면을 다시 그리기 전에 호출되는 단계.

  변경 예정인 새 데이터에 접근가능

  **변경 예정 데이터의 값과 관련된 로직**

**데이터 값을 갱신하는 로직**

### 📌updated

가상 돔으로 다시 화면을 그리고나면 실행되는 단계

데이터 변경으로 인한 화면 요소 변경까지 완료된 시점

**데이터 변경 후 화면 요소 제어와 관련된 로직**

주의) 이 단계에서 데이터 값을 변경하면 무한루프 가능성이 있으므로 computed, watch를 써야함

### 📌beforeDestroy

**뷰 인스턴스의 데이터를 삭제**하기 좋은 단계

### 📌destroyed

하위에 선언한 인스턴스들까지 모두 삭제되는 단계
<br>
<br>

참고 : 📘Do it Vue.js 입문(장기효, 이지스퍼블리싱)
