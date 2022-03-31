---
layout: post
title: [학습] java bean class
---

자바 빈 클래스는 JSP를 이용한 프로그래밍 중에 사용되는 데이터를 저장하기 위해서만 쓰이는 클래스이다.
이전에 자바 UI구성과 오라클 DB를 연동한 프로그램을 만들때 DB에 실제로 접근하는 DAO클래스와(자바코드를 이용하여 연결과 필요한 데이터에 관한 쿼리문을 DB에 직접 전송) 
DAO에서 받은 데이터를 UI에 전달하기 위햬 데이터 저장만 하는 VO 클래스를 이용하였는데 거의 같은 기능을 한다.
아래는 간단한 예제이다.

```
// bean 파일 생성을 위해서 패키지 생성
package com.jongmin.javabeans;

public class MemberBean {
// 변수 선언, 캡슐화를 위해 private로 지정
	private String name;
	private String userid;
	private String nickname;
	private String pwd;
	private String email;
	private String phone;
  
// getter, setter 메소드 이용해서 변수에 값 입,출력 가능하도록 설정
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public String getUserid() {
		return userid;
	}
	public void setUserid(String userid) {
		this.userid = userid;
	}
	public String getNickname() {
		return nickname;
	}
	public void setNickname(String nickname) {
		this.nickname = nickname;
	}
	public String getPwd() {
		return pwd;
	}
	public void setPwd(String pwd) {
		this.pwd = pwd;
	}
	public String getEmail() {
		return email;
	}
	public void setEmail(String email) {
		this.email = email;
	}
	public String getPhone() {
		return phone;
	}
	public void setPhone(String phone) {
		this.phone = phone;
	}
}
```

bean 파일에 접근하기 위해서는 액션태그를 사용하고 scope를 통해 원하는 세션에 객체를 만들 수 있다.

```
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>자바 빈 객체 생성하기(use Bean 액션 태그)</title>
</head>
<body>
<jsp:useBean class=package com.jongmin.javabeans.MemberBean;" id="member"/> // bean 파일을 이용하기 위한 액션태그, 사용하기 위해 id를 설정한다.

자바 빈 객체 생성 후 저장된 정보 출력하기. <br><br>
이름 : <%= member.getName() %> <br>
아이디 : <%= member.getUserid() %>
<hr>

정보 변경한 후 변경된 정보 출력하기. <br><br>
<% 
member.setName("이종민");
member.setUserid("irondrumsky");
%>
이름 :  <%= member.getName() %> <br>
아이디 : <%= member.getUserid() %> 
</body>
</html>
```

[위 내용은 로드북 출판사 백견불여일타 JSP&Servlet을 보고 참고한 내용입니다.]
