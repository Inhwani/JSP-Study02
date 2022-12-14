## 내장 객체 영역

웹에서는 페이지들이 모여 하나의 요청(Request)을 처리

요청들이 모여 하나의 세션(Session)

세션들이 모여 하나의 웹 애플리케이션을 이룸.

## 3.1 내장 객체의 영역

내장 객체의 영역은 각 객체가 저장되는 메모리의 유효기간.

JSP에서는 영역을 통해 내장 객체에 저장된 속성값을 공유할 수 있도록 함.

내장객체의 영역 총 4가지
- page 영역: 동일한 페이지에서만 공유
- request 영역: 하나이 요청에 의해 호출된 페이지와 포워드(요청 전달)된 페이지까지 공유
- session 영역: 클라이언트가 처음 접속한 후 웹 브라우저가 닫을 때까지 공유
- application 영역: 한 번 저장되면 웹 애플리케이션이 종료될 때까지 유지.

Application > Session > Request > Page

이들의 사용법(API)은 모두 같음

## Void setAttribute(String name, Object value)
- 각 영역에 속성을 저장
- 첫 번째 인수는 속성명, 두 번째 인수는 저장할 값
- 값의 타입은 Object이므로 모든 타입의 객체를 저장 할 수 있음.

## Object getAtrribute(String name)
- 영역에 저장된 속성값을 얻어옴
- Object로 자동 형변환되어 저장되므로 원래 타입으로 형변환 후 사용해야 함.

## void removeAttribute(String name)
- 영역에 저장된 속성을 삭제함.
- 삭제할 속성명이 존재하지 않더라도 에러는 발생하지 않음.

## 3.2 데이터 전송 객체(DTO) 준비

DTO란 주로 데이터를 저장하거나 전송하는데 쓰이는 객체로, 다른 로직 없이 순수하게 데이터만을 담고 있음.

데이터만 가지고 있는 객체라 하여 값 객체라고도 함. DTO는 자바빈즈 규약에 따라 작성

## 자바 빈즈 규약
- 자바빈즈는 기본 패키지 이외의 패키지에 속해야 함.
- 멤머 변수의 접근 지정자는 private으로 선언
- 기본 생성자가 있어야 함.
- 멤버 변수에 접근할 수 있는 게터/ 세터 메서드가 있어야 함.
- 게터 / 세터 메서드의 접근 지정자는 public으로 선언함.

## 3.3 Page 영역

page 영역은 클라이언트의 요청을 처리하는 데 관여하는 jsp 페이지마다 하나씩 생성됨.

각 jsp 페이지는 page 영역을 사용하기 위한 pageContext 객체를 할당 받게 됨.

pageContext는 내장 객체 중 하나. 저장된 정보는 해당 페이지에서만 사용 가능

## request 영역

클라이언트가 요청을 할 때마다 새로운 request 객체가 생성되고, 같은 요청을 처리하는 데 사용되는 모든 JSP 페이지가 공유함.

따라서 request 영역에 저장된 정보는 현재 페이지와 포워드된 페이지까지 공유할 수 있음

page 영역보다는 접근 범위가 조금 더 넓음.

## 3.5 Session 영역

클라이언트가 웹 브라우저를 최초로 열고난 후 닫을 때까지 요청되는 모든 페이지는 Session 객체를 공유할 수 있음.

Session이란 클라이언트가 서버에 접속해 있는 상태 혹은 단위를 말함. 주로 회원인증 후 로그인 상태를 유지하는 처리에 사용.

## 3.6 application 영역

웹 애플리케이션은 단 하나의 application 객체만 생성하고, 클라이언트가 요청하는 모든 페이지가 application  객체를 공유하게 됨.

웹 서버를 내릴때 삭제 됨.
