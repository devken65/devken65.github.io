---
title: "JQuery Form Element / AJAX / (보강)CSS"
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
**메소드**  
  
| 옵션 | 설명 |  
| ------- | --------------------------------------------------------- |  
| .val()  | 선택한 요소의 값을 가져오거나, 새로운 값을 적용 |  
| .prop() | 선택한 요소의 상태 속성 값을 가져온다 |  
| .attr() | attribute, 요소의 속성값을 가져오거나 새로운 값으로 지정. |  
  
.val()은 양식(form)의 내용물을 가져오거나 값을 설정하는 메소드이다.    
```html
<input id="myname" type="text" value="홍길동">
```
```javascript
$("input").val();        // "홍길동" (가져오기)
$("input").val("김철수"); // 입력값을 김철수로 바꿈

$("#myname").val();        // id으로 값을 찾아오기
$("#myname").val("김네모"); 
```

.prop()은 현재 상태 ( ON / OFF 같은 상태를 말함 )   
```html
<input type="checkbox" checked>
```
```javascript
$("input").prop("checked");      // true (지금 체크됨?)
$("input").prop("checked", true); // 체크 상태로 만들기
```
  
.prop을 응용하여 전체선택 / 해제를 만들어 볼 수 있다.    
또한, 주로 Radio / CheckBox 에 자주 쓴다.   
   
.attr()은 HTML에 적혀 있는 속성 문자열을 말한다.    
요소의 속성값을 가져오거나 새로운 값으로 지정 가능하다.  
```html
<input type="text" value="홍길동">
```
```javascript
$("input").attr("value");        // "홍길동" (HTML에 적힌 값)
$("input").attr("value", "영희"); // HTML 속성 자체 변경
```
select의 선택된 값을 가져오거나, 설정할 수 있고, 항목 변경 시 다양한 작업  
.val() 을 이용한 select 된 값을 가져오고, .on()을 결합해 function을 실행가능  

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
ajax는 필요한 데이터만을 불러와 정제해서 사용할 수 있다.    

ajax 예제 - 데이터 전달 ( 이벤트 발생 시 ajax 실행 까지 )  


### 🟡 보강
#### 🟡 배경 속성 위치, 크기, 그라데이션
CSS 레이아웃인 박스는 콘텐츠 영역과 테두리, 여백들로 구성된다.    
실제 콘텐츠 영역, 박스와 콘텐츠 영역 사이의 여백 패딩, 박스의 테두리(보더), 박스 모델 사이의 여백인 마진 으로 구성된다.   

#### 🟡 박스 래밸 요소
블록 레벨 요소 : 태그를 사용해 컨텐츠를 추가했을 때 한 줄을 통째로 차지하는 요소이다.  양 옆으로 다른 요소가 올 수 없는 것 ( 너비, 마진, 패딩으로 크기나 위치를 지정 할 수 있다. )  
인라인 레벨 요소 : 화면의 표시되는 컨텐츠만큼만 차지하는 요소  

#### 🟡 display 속성
필요에 따라 인라인 및 블록 레벨을 변경할 수 있다.  
  
block : 해당 요소를 블록 레벨로 지정함
inline : 인라인 요소로 지정
inline-block : 인라인 요소로 지정하면서 내용은 블록 레벨 속성을 적용
none : 화면에 전혀 표시되지 않게 함.

#### 🟡 테두리 관련 속성
border-style  
박스의 테두리 스타일을 지정한다.  
  
border-width  
테두리의 두께를 지정함   
  
border-color  
박스의 테두리 색상  
  
border-radius  
박스 모서리의 둥근 정도를 조절할 수 있음  

#### 🟡 여백관련 속성 
margin - 바깥쪽 여백  
padding - 안쪽 여백  

#### 🟡 float
- 웹 요소를 문서 위에 떠 있는 상태로 만든다
- 요소의 왼쪽 구석 혹은 오른쪽 구석에 요소가 배치된다는 것

#### 🟡 clear 
- 한 번 float을 이용해 배치를 결정하면 그 다음에 넣는 요소도 똑같은 속성이 전달된다. 

#### 🟡 position
- 웹 문서 안의 요소들을 자유자재로 배치해주는 속성  
- 텍스트나 이미지를 나란히 배치하거나 여러 개의 요소를 가로 세로 원하는 위치에 배치  

static : 기본 값 ( 문서 흐름에 맞추어 배치 )  
relative : 이전 요소에 자연스럽게 연결해 배치하는데 위치 지정 가능  
absolute : 원하는 위치 지정해 배치  
fixed : 지정한 위치에 고정해 배치, 브라우저 기준.  

- static을 제외한 나머지 속성값에서 상하좌우 위치조절 가능 

#### 🟡 visibility
- 특정 요소를 화면에 보이게 하거나 보이지 않게 혹은 겹치게 설정하는 속성  
visible : 기본 값 ( 화면에 요소 표시 )  
hidden : 요소 감춤 ( 크기는 그대로 배치에 영향을 미친다. )  

#### 🟡 z-index
- 한 요소 위에 다른 요소 쌓기 위해 순서를 지정   
- 값이 작을수록 아래에 쌓이고 값이 클수록 위에 쌓인다    
- 명시하지 않을경우 제일 먼저 삽입된 요소가 1을 가지고, 그 후에 추가되는 요소들은 값이 점점 커진다.   