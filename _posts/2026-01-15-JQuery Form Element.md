---
title: "JQuery 셀렉팅 심화 / 이벤트"
excerpt: ""

categories:
  - jquery

tags:
  - [jquery]

toc: true
toc_sticky: true

date: 2026-01-15
last_modified_at: 2026-01-15

description: 
---

## 🔴 Form Element
val() - 선택한 요소의 값을 가져오거나, 새로운 값을 적용

hr 태그랑 br 태그의 차이? 

select의 선택된 값을 가져오거나, 설정할 수 있고, 항목 변경 시 다양한 작업
.val() 을 이용한 select 된 값을 가져오고, .on()을 결합해 function을 실행가능.

.prop() - 선택한 요소의 상태 속성 값을 가져옴 
( 주로 Radio / Checkbox 가 선택된 개수를 가져온다. )
( 이걸 응용해 전체선택 및 해제를 할 수 있다. )

.attr() - attribute 약자, 요소의 속성값을 가져오거나 새로운 값으로 지정 가능.

페이지 : 148

## 🟠 AJAX
JQuery 를 하면 뺴놓을 수 없는 AJAX
- 일반적인 HTTP 요청 - 동기방식
- AJAX 요청 - 비동기방식 ( 항상 최신 데이터를 받아온다 )
( 대표적으로 유튜브 )

AJAX 는 URL로 리프레시를 보냈을때 티가 안난다.
- json 데이터 바인딩 ( 가상 데이터를 불러와 테이블로 )
json 언급 - Javascript Object Notation
데이터를 전달할 때 사용하는 표준 형식 ( 보내고 받을 때 서로 약속, 틀)
json은 속성(key) / 값(value) 가 하나의 쌍을 이루고 있는 텍스트 데이터

mockaroo(https://mockaroo.com/) <- 샘플 json 파일 생성

html 요청은 모든 데이터를 불러오지만,
ajax는 필요한 데이터만을 불러와 정제해서 사용할 수 있구나 다

ajax 예제 - 데이터 전달 ( 이벤트 발생 시 ajax 실행 까지 )


### 🟡 DOM 다루기 / 객체 편집 메소드




