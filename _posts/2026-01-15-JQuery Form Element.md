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

AJAX 는 URL로 리프레시를 보냈을때


### 🟡 DOM 다루기 / 객체 편집 메소드
JQuery 으로 요소를 동적으로 추가할 수 있다. ( 어디에 끼워넣고 / 없애고 )
```html
<html>
  <head>
    <!--JQuery 셋팅-->
    <script type="text/javascript" src="https://code.jquery.com/jquery-3.1.1.min.js"></script>
    <script>
        $(document).ready(function(){
          var price = $('<p>From $399.99</p>');
        });
    </script>
  </head>
  <body>
    ...
  </body>
</html> 
```
객체 편집 메소드  
| 옵션 | 설명 |  
| ------- | ------- |  
| $("선택한 요소").append("추가할 요소")   | 선택한 요소 안에 들어가서, 제일 마지막 자식으로 추가.  
| $("선택한 요소").prepend("추가할 요소")   | 선택한 요소 안에 들어가서, 제일 첫번째 자식으로 추가.  
| $("선택한 요소").after("추가할 요소")   | 선택한 요소의 다음(뒤) 요소로 추가.  
| $("선택한 요소").before("추가할 요소")   | 선택한 요소의 이전(앞) 요소로 추가.  
| $("삭제할 요소").remove()   | 선택한 요소를 삭제(자식까지 모두)  

> JQuery 으로 요소를 추가할 때에는, html 혹은 문자열을 그대로 넣는 것이 아닌 JQuery의 문법에 맞추어서 넣는 것이 중요하다.   
{: .prompt-tip}  

### 🟡 with 이벤트 ( 추후 정리 )
클릭 이벤트  
- .on('click', function(){<기능>}) - 요소가 마우스 클릭을 감지하면 <기능>을 실행

반복되는 요소에 각각 이벤트를 적용하기 위해, 코드 작성 시에는 항상 개별 셀렉팅이 필수이다.  (..개별 셀렉팅 방법 좀 쓰면 좋을듯)

### 🟡 보강 ( 추후 정리 )
form 태그에 관해..
get도 데이터를 넘긴다. 
다만, get은 주소창에 정보가 다 표시되고 넘기는 것도 한정적.
post는 보안이 좀 더 추가되었다고 생각하면 되고, 정보 길이에도 제한이없으며 입력한 내용이 드러나지 않는다.

action
target은 특별한 경우 아니면 쓰지 않는다. target="_top" 
top이라고 정해둔 브라우저에서 쓰임

label - 폼 요소에 레이블을 붙이기 위함
(이 라벨은 후에 나오는 인풋태그등에 붙이면 를 위한 라벨이야)
fieldset - form을 하나로 묶어줌
legend - fieldset의 이름을 붙여줌 

input의 type 속성에 사용하는 유형
hidden - 사용자에겐 안보이고 서버에 남는 값 
text - 한 줄짜리 텍스트를 입력하는 상자
checkbox - 2개 이상 선택가능
radio - 둘중하나

form은 내부에 form을 쓰진못하고, 중첩으로 쓸라믄 따로 분리해서 써야함 ( 한 페이지 내에서 다중 form을 쓰고싶을 시 )

autofocus - 페이지 호출 시 첫번째로 작성해야함 ( 깜빡깜빡 )
( 웹 에디터로 하면, 브라우저의 기능이 100% 구현이 아니라 안될수도 )

required - 필수로 입력하는 강제성을 부여함

selectbox multiple - 펼쳐져있는 셀렉트박스, 여러개 선택 가능하다.
optgroup - 셀렉박스 내용이 많을때, 제목처럼 지정가능 ( label )
option - value, 내용까지 함께 씀 submit으로 제출 시 value 값이 넘어간다.

### 보강 CSS
CSS 시트를 html에 포함하는 방법
내부 스타일 시트 ( head 태그 안에 작성 )
외부 스타일 시트 ( 링크로, 역시 html, 대신 파일 분리 )
인라인 스타일 ( html 태그랑 함께 )

### 선택자
* - 전체 
태그로 선택
클래스 선택
id 선택 - 문서 안에서 한 번만 적용

### 폰트
font-size 에서 잘 쓰는 단위 : em, px
1em == 16px, px은 모니터에 따라 상대적 크기를 말함.
em은 해당 글꼴의 대문자 M의 너비를 기준으로 크기 조절

### 색상 표현 방법
16진수, rgb, hsl 혹은 색상이름 표기



